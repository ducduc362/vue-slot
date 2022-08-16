<template>
  <div id="app" class="px-5">
    <select
      v-model="selected"
      class="form-select mb-4 px-3"
      aria-label="Default select example"
    >
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
      >
        {{ option.label }}
      </option>
    </select>
    <AppUserList>
      <template #userlist="{ users, remove }">
        <AppUserCardList :list="users">
          <template #[selected]="{ text }"
            ><h5>{{ text }}</h5></template
          >
          <template #secondrow="{ item }">
            <AppButton :typeButton="'danger'" @click="remove(item)">
              Remove
            </AppButton>
          </template>
        </AppUserCardList>
      </template>
      <template #loading>
        <AppSpinner />
      </template>
    </AppUserList>
  </div>
</template>

<script>
import AppUserList from "@/components/AppUserList.vue";
import AppSpinner from "@/components/AppSpinner.vue";
import AppButton from "@/components/AppButton.vue";
import AppUserCardList from "@/components/AppUserCardList.vue";

export default {
  name: "App",
  components: {
    AppUserList,
    AppSpinner,
    AppButton,
    AppUserCardList,
  },
  data() {
    return {
      selected: "first",
      options: [
        { value: "first", label: "First Name" },
        { value: "last", label: "Last Name" },
        { value: "full", label: "Fullname" },
        { value: "fullWidthTitle", label: "Fullname With Title" },
      ],
    };
  },
  methods: {
    log() {
      console.log("Hi!");
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
