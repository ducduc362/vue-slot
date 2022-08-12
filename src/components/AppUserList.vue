<template>
  <section>
    <slot name="title"><h1>Users</h1></slot>
    <slot
      name="userlist"
      :count="data.results.length"
      :userlist="data.results"
      :remove="remove"
      v-if="state === 'loaded'"
    >
      <ul class="userlist row">
        <li class="col-4" v-for="item in data.results" :key="item.email">
          <slot name="listitem" :user="item">
            <div>
              <img
                width="48"
                height="48"
                :src="item.picture.large"
                :alt="item.name.first + ' ' + item.name.last"
              />
              <div>
                <div>{{ item.name.first }}</div>
                <slot name="secondrow" :item="item" :remove="remove">haha</slot>
              </div>
            </div>
          </slot>
        </li>
      </ul>
    </slot>
    <slot v-if="state === 'loading'" name="loading">Loading...</slot>
    <slot v-if="state === 'failed'" name="error">
      <p>Oops, something went wrong!</p>
    </slot>
  </section>
</template>

<script>
const states = {
  idle: "idle",
  loading: "loading",
  loaded: "loaded",
  failed: "failed",
};
export default {
  data() {
    return {
      state: "idle",
      data: undefined,
      error: undefined,
      states,
    };
  },
  mounted() {
    this.load();
  },
  methods: {
    async load() {
      this.state = "loading";
      this.error = undefined;
      this.data = undefined;
      try {
        const response = await fetch("https://randomuser.me/api/?results=5");
        const json = await response.json();
        this.state = "loaded";
        this.data = json;
        return response;
      } catch (error) {
        this.state = "failed";
        this.error = error;
        return error;
      }
    },

    remove(item) {
      this.data.results = this.data.results.filter(
        (el) => el.email !== item.email
      );
      return this.data.results;
      //   console.log(this.data);
    },
  },
};
</script>

<style>
.userlist {
  margin: 10px;
}
.userlist img {
  border-radius: 50%;
  margin-right: 1rem;
}
.userlist li + li {
  margin-top: 10px;
  list-style: none;
}
.userlist li > div {
  display: flex;
  align-items: center;
}
.userlist li div div {
  flex: 1;
}
</style> 