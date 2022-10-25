<template>
  <PlainCalculator class="hola"/>
</template>

<script>
import PlainCalculator from "@/components/Calculator";

export default {
  name: 'App',
  components: {
    PlainCalculator,
  }
}
</script>

<style>

*{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: aliceblue;
  padding: 0;
  margin: 0;
}
</style>
