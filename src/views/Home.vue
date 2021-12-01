<template>
  <div class="home">
    <h1>Javascript Watcher</h1>
    <h2>Vue</h2>
    <h5>Stars: {{ vue.watchers }}</h5>
    <h5>Watchers: {{ vue.subscribers_count }}</h5>
    <h5>Forks: {{ vue.forks }}</h5>
    <h2>Angular</h2>
    <h5>Stars: {{ angular.watchers }}</h5>
    <h5>Watchers: {{ angular.subscribers_count }}</h5>
    <h5>Forks: {{ angular.forks }}</h5>
    <h2>Ember</h2>
    <h5>Stars: {{ ember.watchers }}</h5>
    <h5>Watchers: {{ ember.subscribers_count }}</h5>
    <h5>Forks: {{ ember.forks }}</h5>
    <h2>Svelte</h2>
    <h5>Stars: {{ svelte.watchers }}</h5>
    <h5>Watchers: {{ svelte.subscribers_count }}</h5>
    <h5>Forks: {{ svelte.forks }}</h5>
    <h2>React</h2>
    <h5>Stars: {{ react.watchers }}</h5>
    <h5>Watchers: {{ react.subscribers_count }}</h5>
    <h5>Forks: {{ react.forks }}</h5>
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
      axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
        this.vue = response.data;
        console.log("Vue stats", this.vue);
      });
    },
    gitHubIndexAngular: function () {
      axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
        this.angular = response.data;
        console.log("Angular stats", this.angular);
      });
    },
    gitHubIndexEmber: function () {
      axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
        this.ember = response.data;
        console.log("Ember stats", this.ember);
      });
    },
    gitHubIndexSvelte: function () {
      axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
        this.svelte = response.data;
        console.log("Svelte stats", this.svelte);
      });
    },
    gitHubIndexReact: function () {
      axios.get("https://api.github.com/repos/facebook/react").then((response) => {
        this.react = response.data;
        console.log("React stats", this.react);
      });
    },
  },
};
</script>
