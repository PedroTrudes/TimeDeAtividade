<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Forms />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Forms from './components/Forms.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Forms
  }
});
</script>

<style>

</style>
