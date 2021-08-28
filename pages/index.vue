<template>
  <div class="roulette">
    <h1>気分転換ルーレット</h1>
    <p>気分が乗らない...</p>
    <button @click="spinRoulette">そんな時は</button>
    <h2 v-if="showBreak">{{ selectedBreak }}だ！</h2>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { breaks } from '~/assets/breaks'

export default Vue.extend({
  data() {
    const showBreak: boolean = false
    const randomIndex: number = 0

    return {
      showBreak,
      randomIndex,
    }
  },
  computed: {
    selectedBreak(): string {
      return breaks[this.randomIndex]
    },
  },
  methods: {
    spinRoulette() {
      this.randomIndex = Math.floor(Math.random() * breaks.length)
      this.showBreak = true
    },
  },
})
</script>

<style>
.roulette {
  width: 400px;
  margin: 0 auto;
}
</style>
