<template>
  <div id="app">
    <div class="office">
      <Map @closeProfile="closeProfile" @openProfile="openProfile" />
      <SideMenu :isUserOpenned.sync="isUserOpenned" :person="person" />
    </div>
  </div>
</template>

<script>
import Map from "./components/Map.vue";
import SideMenu from "./components/SideMenu.vue";

export default {
  name: "App",
  data: () => ({
    isUserOpenned: false,
    person: {},
  }),
  components: {
    Map,
    SideMenu,
  },
  methods: {
    openProfile(person) {
      this.isUserOpenned = true;
      this.person = person;
    },
    closeProfile() {
      this.isUserOpenned = false;
      this.person = null;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  background-color: #fafafa;
  padding: 24px;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
}

* {
  box-sizing: border-box;
}

h3 {
  margin-top: 0;
}

.office {
  display: grid;
  grid-template-columns: 1fr 450px;
  border-radius: 6px;
  border: 1px solid #ccd8e4;
  height: 100%;
  background: white;
  max-width: 1500px;
  margin: 0 auto;
}
</style>
