<template>
  <div class="home">
    <h1>Javascript Watcher</h1>
    <h2>Vue</h2>
    <h5>Stars: {{ vue.items[0].watchers }}</h5>
    <h5>Watchers: ?</h5>
    <h5>Forks: {{ vue.items[0].forks }}</h5>
    <h2>Angular</h2>
    <h5>Stars: {{ angular.items[1].watchers }}</h5>
    <h5>Watchers: ?</h5>
    <h5>Forks: {{ angular.items[1].forks }}</h5>
    <h2>Ember</h2>
    <h5>Stars: {{ ember.items[0].watchers }}</h5>
    <h5>Watchers: ?</h5>
    <h5>Forks: {{ ember.items[0].forks }}</h5>
    <h2>Svelte</h2>
    <h5>Stars: {{ svelte.items[0].watchers }}</h5>
    <h5>Watchers: ?</h5>
    <h5>Forks: {{ svelte.items[0].forks }}</h5>
    <h2>React</h2>
    <h5>Stars: {{ react.items[0].watchers }}</h5>
    <h5>Watchers: ?</h5>
    <h5>Forks: {{ react.items[0].forks }}</h5>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  components: {},
  data: function () {
    return {
      vue: {},
      angular: {},
      ember: {},
      svelte: {},
      react: {},
    };
  },
  created: function () {
    this.gitHubIndexVue();
    this.gitHubIndexAngular();
    this.gitHubIndexEmber();
    this.gitHubIndexSvelte();
    this.gitHubIndexReact();
  },
  methods: {
    gitHubIndexVue: function () {
      axios.get("https://api.github.com/search/repositories?q=vue").then((response) => {
        this.vue = response.data;
        console.log("Vue stats", this.vue);
      });
    },
    gitHubIndexAngular: function () {
      axios.get("https://api.github.com/search/repositories?q=angular").then((response) => {
        this.angular = response.data;
        console.log("Angular stats", this.angular);
      });
    },
    gitHubIndexEmber: function () {
      axios.get("https://api.github.com/search/repositories?q=ember").then((response) => {
        this.ember = response.data;
        console.log("Ember stats", this.ember);
      });
    },
    gitHubIndexSvelte: function () {
      axios.get("https://api.github.com/search/repositories?q=svelte").then((response) => {
        this.svelte = response.data;
        console.log("Svelte stats", this.svelte);
      });
    },
    gitHubIndexReact: function () {
      axios.get("https://api.github.com/search/repositories?q=react").then((response) => {
        this.react = response.data;
        console.log("React stats", this.react);
      });
    },
  },
};
</script>
