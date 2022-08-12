<template>
  <div id="app">
    <AppUserList>
      <template #userlist="{ userlist }">
        <AppUserCardList :list="userlist">
          <template #secondrow="{ item, remove }">
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
import AppUserList from "./components/AppUserList.vue";
import AppSpinner from "./components/AppSpinner.vue";
import AppButton from "./components/AppButton.vue";
import AppUserCardList from "./components/AppUserCardList.vue";

export default {
  name: "App",
  components: {
    AppUserList,
    AppSpinner,
    AppButton,
    AppUserCardList,
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
