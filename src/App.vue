<template>
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>First Match: {{ firstMatch }}</h1>
    <h1 :class="secondMatch >= 10 ? 'text-red' : 'text-gray'">Second Match: {{ secondMatch }}</h1>
    <h1 v-if="secondMatch >= 10">
        Result: {{ firstMatch + secondMatch }}
    </h1>
    <h1 v-else>
        Second match kurang dari 10
    </h1>

    <button @click="firstMatch += 1">Tambah first match</button>
    <br>
    <br>
    <button @click="secondMatch += 1">Tambah second match</button>
    <br>
    <br>

    <input v-model="scoreFromUser" type="text" name="input-score" id="input-score" placeholder="Masukkan score">
    <button @click="pushDatatoArray()">Tambahkan data</button>
    <h1>Perolehan nilai sementara</h1>
    <p v-for="(score, s) in scores" :key="s">{{ score }}</p>
    {{ scores }}
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
        firstMatch: 0,
        secondMatch: 0,
        scores: [ 12, 21, 20, 15 ],
        scoreFromUser: 0,
    }
  },
  methods: {
    pushDatatoArray() {
        this.scores.push(parseFloat(this.scoreFromUser));
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.text-red {
    color: red;
}
.text-gray {
    color: gray;
}
</style>
