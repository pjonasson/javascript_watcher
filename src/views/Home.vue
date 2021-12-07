<template>
  <div class="home">
    <div class="container1">
      <h1 class="title animate__bounceIn">Javascript Framework Watcher</h1>
    </div>
    <div class="container">
      <div class="block col-lg-4">
        <h2>Stars</h2>
        <pure-vue-chart
          class=""
          v-if="watchers.length > 0"
          :max-y-axis="250000"
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
          barColor="lightgreen"
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
          :max-y-axis="50000"
          :show-y-axis="true"
          :show-x-axis="true"
          :points="forks"
          :width="400"
          :height="300"
          barColor="lightpink"
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
    <div class="container text-align-center">
      <div class="block col-lg-2">
        <h2>
          <a href="https://github.com/vuejs/vue">Vue</a>
        </h2>
        <img
          class="logo"
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/440px-Vue.js_Logo_2.svg.png"
          alt=""
        />
        <h5>&#11088;s: {{ vueWatcher[0] }}</h5>
        <h5>&#128064;s: {{ vueSubscribers[0] }}</h5>
        <h5>&#9282;s: {{ vueForks[0] }}</h5>
      </div>
      <div class="block col-lg-2">
        <h2>
          <a href="https://github.com/angular/angular.js">Angular</a>
        </h2>
        <img
          class="logo"
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTvDdnYY_s2WR_D0jYWwESo2AL9oOHgeFxUtIARamqFFn6qgHUSVdHPdP9ECz-TwhhKZ8Y&usqp=CAU"
          alt=""
        />
        <h5>&#11088;s: {{ angularWatcher[0] }}</h5>
        <h5>&#128064;s: {{ angularSubscribers[0] }}</h5>
        <h5>&#9282;s: {{ angularForks[0] }}</h5>
      </div>
      <div class="block col-lg-2">
        <h2>
          <a href="https://github.com/emberjs/ember.js/">Ember</a>
        </h2>
        <img
          class="logo"
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTpglW6qWmm8dA-gAq6kiZawzAtbl-AL5sLUG9hsE0n51F188QpkC3j4zCbfLvAiLlcIAo&usqp=CAU"
          alt=""
        />
        <h5>&#11088;s: {{ emberWatcher[0] }}</h5>
        <h5>&#128064;s: {{ emberSubscribers[0] }}</h5>
        <h5>&#9282;s: {{ emberForks[0] }}</h5>
      </div>
      <div class="block col-lg-2">
        <h2>
          <a href="https://github.com/sveltejs/svelte">Svelte</a>
        </h2>
        <img
          class="logo"
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRe1WQvtM9H-SYQs-0eC68aANfML_U-7T61eaq5XadTH8GXd0vcddbE2RUm0KidpqWBDtY&usqp=CAU"
          alt=""
        />
        <h5>&#11088;s: {{ svelteWatcher[0] }}</h5>
        <h5>&#128064;s: {{ svelteSubscribers[0] }}</h5>
        <h5>&#9282;s: {{ svelteForks[0] }}</h5>
      </div>
      <div class="block col-lg-2">
        <h2>
          <a href="https://github.com/facebook/react">React</a>
        </h2>
        <img
          class="logo"
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS18-Pl_EL3TuQIrxLsgthdm9apJlkrXa8cty4Km6qr9HHCUw00ZxSmoRz2tpPSqSKmSS8&usqp=CAU"
          alt=""
        />
        <h5>&#11088;s: {{ reactWatcher[0] }}</h5>
        <h5>&#128064;s: {{ reactSubscribers[0] }}</h5>
        <h5>&#9282;s: {{ reactForks[0] }}</h5>
      </div>
      <div class="block col-lg-2">
        <h2>Totals</h2>
        <img
          class="logo"
          src="https://www.freepnglogos.com/uploads/javascript-png/javascript-logo-transparent-logo-javascript-images-3.png"
          alt=""
        />
        <h5>&#11088;s: {{ watchersSum[0] }}</h5>
        <h5>&#128064;s: {{ subscribersSum[0] }}</h5>
        <h5>&#9282;s: {{ forksSum[0] }}</h5>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import PureVueChart from "pure-vue-chart";
import "animate.css";

export default {
  props: {
    animationDuration: { type: Number, default: 5 },
  },
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
      watchersSum: [],
      subscribersSum: [],
      forksSum: [],
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
    this.watchersTotal();
    this.subscribersTotal();
    this.forksTotal();
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
    watchersTotal: function () {
      var sum = 0;
      for (let i = 0; i < this.watchers.length; i++) {
        sum += this.watchers[i];
      }
      this.watchersSum.push(sum);
      console.log(sum);
    },
    subscribersTotal: function () {
      var sum = 0;
      for (let i = 0; i < this.subscribers.length; i++) {
        sum += this.subscribers[i];
      }
      this.subscribersSum.push(sum);
      console.log(sum);
    },
    forksTotal: function () {
      var sum = 0;
      for (let i = 0; i < this.forks.length; i++) {
        sum += this.forks[i];
      }
      this.forksSum.push(sum);
      console.log(sum);
    },
  },
};
</script>

<style>
a:link {
  color: green;
  background-color: transparent;
  text-decoration: none;
}

a:visited {
  color: rgb(1, 5, 2);
  background-color: transparent;
  text-decoration: none;
}
h1 {
  font-family: monospace, monaco;
}
h2 {
  font-family: monospace, monaco;
}

.logo {
  height: 70px;
  width: 70px;
  padding-bottom: 10px;
}
.block {
  text-align: center;
}
</style>
