<template>
  <div class="generator">
    <form @submit.prevent="calculate" v-if="!isGenerate">
      <p>
        Amount of numbers need to be generated: <input  v-model="number2Generate" type="number"/>
      </p>

      <h3>Range of the number</h3>
      <div class="inputs">
        min: <input v-model="min" type="number" />
        max: <input v-model="max" type="number" />
      </div>

      <button type="submit">Generate!</button>
    </form>
    <div v-else>
      <div v-for="number in numbers" track-by="$index" class="number">
        {{ number }}&nbsp;
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      number2Generate: 0,
      isGenerate: false,
      min: 0,
      max: 0,
      numbers: []
    }
  },
  methods: {
    calculate () {
      this.isGenerate = true

      for (let i = 0; i < this.number2Generate; i++) {
        this.numbers.push(Math.floor(Math.random() * (this.max - this.min + 1)) + this.min)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: #42b983;
}

.inputs {
  display: block;
}

.number {
  display: inline-block;
}
</style>
