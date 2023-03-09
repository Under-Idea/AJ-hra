<template>
  <div class="column">
    <h1>Who</h1>
    <div class="cells">
      <div class="cell" v-for="item in who" v-on:click="handleClick(item, 'who', $event)" :class="[item.hidden === false ? 'active' : 'non-active', (item.hidden === false && item.name !== active_who) ? 'alreadybeen' : '']">
        <p v-if="!item.hidden">{{ item.name }}</p>
        <p v-if="item.hidden">?</p>
      </div>
    </div>
  </div>
  <div class="column">
    <h1>What is he/she doing</h1>
    <div class="cells">
      <div class="cell" v-for="item in verb" v-on:click="handleClick(item, 'verb', $event)" :class="[item.hidden === false ? 'active' : 'non-active', (item.hidden === false && item.name !== active_verb) ? 'alreadybeen' : '']">
        <p v-if="!item.hidden">{{ item.name }}</p>
        <p v-if="item.hidden">?</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      who: [
        {name : "Neighbour", hidden : true},
        {name : "Cleaner", hidden : true},
        {name : "Garbage collector", hidden : true},
        {name : "Teacher", hidden : true},
        {name : "Doctor", hidden : true},
        {name : "Seller", hidden : true},
        {name : "Cook", hidden : true},
        {name : "Writer", hidden : true},
        {name : "Singer", hidden : true},
        {name : "Driver", hidden : true}
      ].sort((a, b) => 0.5 - Math.random()),
      verb: [
        {name : "Find", hidden : true},
        {name : "try", hidden : true},
        {name : "parting", hidden : true},
        {name : "Think", hidden : true},
        {name : "Say", hidden : true},
        {name : "Do", hidden : true},
        {name : "Make", hidden : true},
        {name : "Know", hidden : true},
        {name : "Take", hidden : true},
        {name : "Get", hidden : true}
      ].sort((a, b) => 0.5 - Math.random()),
      Choosing: "who",
      active_who : "",
      active_verb : ""
    };
  },
  methods: {
    handleClick(item, choosed, event) {
      if(choosed === this.Choosing) {
        if(item.hidden) {
          if(choosed === "who") {
            this.Choosing = "verb"
            this.active_who = item.name
          } else if(choosed === "verb") {
            this.Choosing = "who"
            this.active_verb = item.name
          }
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
