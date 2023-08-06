<script>
import { toRaw } from "vue";

export default {
  name: "HelloWorld",

  data() {
    return {
      count: 0,
    };
  },
  props: {
    title: { type: String, default: "" },
    desc: { type: String, default: "" },
    games: { type: Array, default: [] },
    times: { type: Number, default: 0 },
    onPlusTimes: { type: Function },
  },
  computed: {
    filteredGames() {
      return this.games.filter((item) => {
        return item.active == true;
      });
    },
    computedCount() {
      return this.count + 20;
    },
  },

  methods: {
    alertOnClick(index) {
      alert(this.games[index].name);
    },

    filterPlayerByScore(dataPlayers) {
      if (dataPlayers) {
        let newData = toRaw(dataPlayers);
        return newData.filter((player) => {
          return player.score > 50;
        });
      }
    },
  },
};
</script>

<template>
  <div class="greetings">
    <h1 @click="onPlusTimes(1)">{{ times }}</h1>
    <h1 class="green">{{ title }}</h1>
    <p>{{ desc }}</p>
    <p>{{ computedCount }}</p>
    <div class="card" v-for="(item, i) in games" :key="item.name">
      <h1 @click="alertOnClick(i)">{{ item.name }}</h1>
      <h1>{{ item.desc }}</h1>
      <h2
        v-for="player in filterPlayerByScore(item.players)"
        :key="players"
        :class="{
          red: player.name == 'GM',
        }"
      >
        {{ player.name }}
      </h2>
    </div>
  </div>
</template>

<style scoped>
.red {
  color: red;
}
</style>

<!-- <script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style> -->
