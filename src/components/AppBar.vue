<template>
  <div>
    <v-app-bar
        app
        color="rgba(0, 0, 0, 0.4)"
        hide-on-scroll
    >
      <v-app-bar-nav-icon class="d-flex d-sm-none" left @click="drawer = true"></v-app-bar-nav-icon>
      <app-link classes="text-h5 text-no-wrap" to="/">AoE IV Analytics</app-link>
      <v-icon class="ml-2 d-none d-sm-inline-flex">mdi-chart-areaspline</v-icon>
      <v-tabs centered class="d-none d-sm-inline-flex justify-center text-white" color="white">
        <v-tab text to="/">Search</v-tab>
        <!--        <v-tab text to="/profile" >Profile</v-tab>-->
        <v-tab text to="/leaderboards">Leaderboards</v-tab>
        <v-tab text to="/randomizer">Random tool</v-tab>
        <v-tab text to="/about">About</v-tab>
      </v-tabs>

      <v-text-field
          v-model="name"
          class="d-none d-md-flex"
          hide-details
          label="Search player name..."
          background-color="rgba(255,255,255,0.2)"
          :disabled="this.$route.name === 'PageSearch'"
          color="white"
          solo
          v-on:keyup.enter="searchId"
      ></v-text-field>
    </v-app-bar>

    <v-navigation-drawer
        v-model="drawer"
        color="rgba(0, 0, 0, 0.9)"
        fixed
        sticky
        left
        temporary
    >
      <v-list
          dense
          nav
          centered
          height="100vh"
      >
        <v-list-item-group
            v-model="group"
            class="align-center justify-center fill-height"
            active-class=""
        >
          <v-list-item to="/">
            <v-list-item-title>Search</v-list-item-title>
          </v-list-item>

          <v-list-item to="/leaderboards">
            <v-list-item-title>Leaderboard</v-list-item-title>
          </v-list-item>

          <v-list-item to="/randomizer">
            <v-list-item-title>Random tool</v-list-item-title>
          </v-list-item>

          <v-list-item to="/about">
            <v-list-item-title>About</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>

</template>

<script>
import AppLink from "@/components/AppLink";

export default {
  name: "AppBar",
  components: {AppLink},
  data() {
    return {
      drawer: false,
      group: null,
      name: null
    }
  },
  computed: {},
  methods: {
    searchId() {
      this.$router.push({
        name: 'PageSearch',
        params: {search: this.name}
      });
    },
  }
}
</script>

<style scoped>
.v-text-field {
  width: 20rem;
}
</style>
