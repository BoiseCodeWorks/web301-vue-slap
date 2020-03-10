<template>
  <div class="home">
    <slapgame person="Billy" />
    <slapgame person="Bobby" />
    <slapgame person="Berta" />
    <slapgame person="Benny" />
  </div>
</template>

<script>
// @ is an alias to /src
import slapgame from "@/components/SlapGame.vue";

export default {
  name: "Home",
  components: {
    slapgame
  }
};
</script>
