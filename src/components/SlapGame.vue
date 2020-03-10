<template>
  <div :class="colorIndicator">
    <h1 v-if="health > 0">{{person}}'s Health: {{health}}</h1>
    <h1 v-else>YOU KILLED IT</h1>
    <div class="d-flex justify-content-around">
      <button class="btn btn-success" @click="attack(1)" :disabled="health == 0">SLAP</button>
      <button class="btn btn-success" @click="attack(5)" :disabled="health == 0">PUNCH</button>
      <button class="btn btn-warning" @click="health = 100" v-if="health == 0">RESET</button>
    </div>
    <div>
      <button
        v-for="special in specials"
        :key="special.name"
        @click="attack(special.value)"
        :disabled="health == 0"
      >{{special.name}}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SlapGame",
  props: {
    person: String
  },
  data() {
    return {
      health: 100,
      specials: [
        { name: "Hadouken", value: 50 },
        { name: "Round House", value: 150 },
        { name: "Magic Missle", value: 4 },
        { name: "Magic Missle2", value: 4 },
        { name: "Magic Missle3", value: 4 },
        { name: "Magic Missle4", value: 4 },
        { name: "Magic Missle5", value: 4 },
        { name: "Magic Missle6", value: 4 },
        { name: "Magic Missle7", value: 4 },
        { name: "Magic Missle8", value: 4 },
        { name: "Magic Missle9", value: 4 },
        { name: "Magic Missle0", value: 4 },
      ]
    };
  },
  computed: {
    colorIndicator() {
      return {
        good: this.health > 50,
        warning: this.health <= 50 && this.health > 0,
        dead: this.health == 0
      };
    }
  },
  methods: {
    attack(val) {
      this.health -= val;
      if (this.health < 0) {
        this.health = 0;
      }
    }
  }
};
</script>

<style>
.good {
  color: green;
}
.warning {
  color: orange;
}
.dead {
  color: red;
}
</style>
