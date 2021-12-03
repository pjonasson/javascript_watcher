<template>
  <div class="home">
    <h1 class="animate__bounceIn">Javascript Framework Watcher</h1>
    <div class="container">
      <div class="block col-lg-4">
        <h2>Stars</h2>
        <pure-vue-chart
          class="animate__bounceIn"
          v-if="watchers.length > 0"
          :max-y-axis="200000"
          :show-y-axis="true"
          :show-x-axis="true"
          :points="watchers"
          :width="400"
          :height="300"
          barColor="lightblue"
        >
          <template v-slot:label="{ barIndex, midPoint, yLabelOffset }">
            <text v-if="barIndex === 0" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Vue</text>
            <text v-if="barIndex === 1" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Angular</text>
            <text v-if="barIndex === 2" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Ember</text>
            <text v-if="barIndex === 3" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Svelte</text>
            <text v-if="barIndex === 4" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">React</text>
          </template>
        </pure-vue-chart>
      </div>
      <div class="block col-lg-4">
        <h2>Watchers</h2>
        <pure-vue-chart
          class="aanimate__fadeInLeftBig"
          v-if="watchers.length > 0"
          :max-y-axis="8000"
          :show-y-axis="true"
          :show-x-axis="true"
          :points="subscribers"
          :width="400"
          :height="300"
          barColor="green"
        >
          <template v-slot:label="{ barIndex, midPoint, yLabelOffset }">
            <text v-if="barIndex === 0" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Vue</text>
            <text v-if="barIndex === 1" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Angular</text>
            <text v-if="barIndex === 2" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Ember</text>
            <text v-if="barIndex === 3" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Svelte</text>
            <text v-if="barIndex === 4" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">React</text>
          </template>
        </pure-vue-chart>
      </div>
      <div class="block col-lg-4">
        <h2>Forks</h2>
        <pure-vue-chart
          class="animate__fadeInLeftBig"
          v-if="watchers.length > 0"
          :max-y-axis="40000"
          :show-y-axis="true"
          :show-x-axis="true"
          :points="forks"
          :width="400"
          :height="300"
          barColor="orange"
        >
          <template v-slot:label="{ barIndex, midPoint, yLabelOffset }">
            <text v-if="barIndex === 0" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Vue</text>
            <text v-if="barIndex === 1" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Angular</text>
            <text v-if="barIndex === 2" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Ember</text>
            <text v-if="barIndex === 3" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">Svelte</text>
            <text v-if="barIndex === 4" :x="midPoint" :y="`${yLabelOffset + 10}px`" text-anchor="middle">React</text>
          </template>
        </pure-vue-chart>
      </div>
    </div>

    <h2>Vue</h2>
    <h5>&#11088;'s: {{ vueWatcher[0] }}</h5>
    <h5>&#128064;'s: {{ vueSubscribers[0] }}</h5>
    <h5>&#9282;'s: {{ vueForks[0] }}</h5>

    <h2>Angular</h2>
    <h5>Stars: {{ angularWatcher[0] }}</h5>
    <h5>Watchers: {{ angularSubscribers[0] }}</h5>
    <h5>Forks: {{ angularForks[0] }}</h5>
    <h2>Ember</h2>
    <h5>Stars: {{ emberWatcher[0] }}</h5>
    <h5>Watchers: {{ emberSubscribers[0] }}</h5>
    <h5>Forks: {{ emberForks[0] }}</h5>
    <h2>Svelte</h2>
    <h5>Stars: {{ svelteWatcher[0] }}</h5>
    <h5>Watchers: {{ svelteSubscribers[0] }}</h5>
    <h5>Forks: {{ svelteForks[0] }}</h5>
    <h2>React</h2>
    <h5>Stars: {{ reactWatcher[0] }}</h5>
    <h5>Watchers: {{ reactSubscribers[0] }}</h5>
    <h5>Forks: {{ reactForks[0] }}</h5>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import PureVueChart from "pure-vue-chart";
import "animate.css";

export default {
  name: "Home",
  components: {
    PureVueChart,
  },
  data: function () {
    return {
      vue: {},
      angular: {},
      ember: {},
      svelte: {},
      react: {},
      vueWatcher: [],
      vueSubscribers: [],
      vueForks: [],
      angularWatcher: [],
      angularSubscribers: [],
      angularForks: [],
      emberWatcher: [],
      emberSubscribers: [],
      emberForks: [],
      svelteWatcher: [],
      svelteSubscribers: [],
      svelteForks: [],
      reactWatcher: [],
      reactSubscribers: [],
      reactForks: [],
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
      },
      watchers: [],
      subscribers: [],
      forks: [],
    };
  },
  async created() {
    const vue = await axios.get("https://api.github.com/repos/vuejs/vue");
    console.log("Vue data", vue.data);
    this.watchers.push(vue.data.watchers);
    this.vueWatcher.push(vue.data.watchers);
    this.subscribers.push(vue.data.subscribers_count);
    this.vueSubscribers.push(vue.data.subscribers_count);
    this.forks.push(vue.data.forks);
    this.vueForks.push(vue.data.forks);
    console.log(this.vueWatcher, this.vueSubscribers, this.vueForks);
    const angular = await axios.get("https://api.github.com/repos/angular/angular.js");
    this.watchers.push(angular.data.watchers);
    this.angularWatcher.push(angular.data.watchers);
    this.subscribers.push(angular.data.subscribers_count);
    this.angularSubscribers.push(angular.data.subscribers_count);
    this.forks.push(angular.data.forks);
    this.angularForks.push(angular.data.forks);
    console.log("Angular data", angular.data);
    const ember = await axios.get("https://api.github.com/repos/emberjs/ember.js");
    this.watchers.push(ember.data.watchers);
    this.emberWatcher.push(ember.data.watchers);
    this.subscribers.push(ember.data.subscribers_count);
    this.emberSubscribers.push(ember.data.subscribers_count);
    this.forks.push(ember.data.forks);
    this.emberForks.push(ember.data.forks);
    console.log("Ember data", ember.data);
    const svelte = await axios.get("https://api.github.com/repos/sveltejs/svelte");
    this.watchers.push(svelte.data.watchers);
    this.svelteWatcher.push(svelte.data.watchers);
    this.subscribers.push(svelte.data.subscribers_count);
    this.svelteSubscribers.push(svelte.data.subscribers_count);
    this.forks.push(svelte.data.forks);
    this.svelteForks.push(svelte.data.forks);
    console.log("Svelte data", svelte.data);
    const react = await axios.get("https://api.github.com/repos/facebook/react");
    this.watchers.push(react.data.watchers);
    this.reactWatcher.push(react.data.watchers);
    this.subscribers.push(react.data.subscribers_count);
    this.reactSubscribers.push(react.data.subscribers_count);
    this.forks.push(react.data.forks);
    this.reactForks.push(react.data.forks);
    console.log("React data", react.data);
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
