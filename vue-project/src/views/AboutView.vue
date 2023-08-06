<script>
import HelloWorld from "../components/HelloWorld.vue";
export default {
  components: { HelloWorld },
  methods: {
    plusTimes(inc) {
      this.times += inc;
    },
  },
  data() {
    return {
      times: 0,
      myGames: [
        {
          name: "pokemon",
          desc: "dsadasdasdadasd",
          active: true,
          players: [
            {
              name: "player 1",
              score: 20,
            },
            {
              name: "player 2",
              score: 60,
            },
            {
              name: "GM",
              score: 100,
            },
          ],
        },
        {
          name: "digimon",
          desc: "dsadasdasdadasd",
          active: false,
        },
      ],
    };
  },
};
</script>
<template>
  <div class="about">
    <h1>This is an ASADSD page</h1>

    <HelloWorld
      title="title"
      desc="desc"
      :games="myGames"
      :onPlusTimes="plusTimes"
      :times="times"
    />
    <h1 @click="plusTimes(-1)">
      {{ times }}
    </h1>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
