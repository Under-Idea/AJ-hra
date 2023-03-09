<template>
  <div class="column">
    <h1>Who</h1>
    <div class="cell" v-for="item in who" v-on:click="handleClick(item, 'who', $event)" :class="item.hidden === false ? 'active' : 'non-active'">
      <p v-if="!item.hidden">{{ item.name }}</p>
      <p v-if="item.hidden">?</p>
    </div>
  </div>
  <div class="column">
    <h1>Verb</h1>
    <div class="cell" v-for="item in verb" v-on:click="handleClick(item, 'verb', $event)" :class="item.hidden === false ? 'active' : 'non-active'">
      <p v-if="!item.hidden">{{ item.name }}</p>
      <p v-if="item.hidden">?</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      who: [{name : "Neighbour", hidden : true}, {name : "House", hidden : true}, {name : "Mouse", hidden : true}, {name : "Mouse", hidden : true}],
      verb: [{name : "Finding", hidden : true}, {name : "trying", hidden : true}, {name : "parting", hidden : true}],
      Choosing: "who",
    };
  },
  methods: {
    handleClick(item, choosed, event) {
      if(choosed === this.Choosing) {
        if(item.hidden) {
          this.Choosing = (choosed === "who") ? "verb" : "who"
          console.log(this.Choosing)
        }
        item.hidden = false
      }
    },
  },
};
</script>

<style scoped>
body {
  color: white;
}
</style>
