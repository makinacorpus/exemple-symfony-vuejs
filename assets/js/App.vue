<script>
export default {
  data() {
    return {
      name: '',
      hello: ''
    }
  },
  methods: {
    refreshHello() {
      if (this.name) {
        fetch("/api/helloword/" + this.name, {"method": "GET"})
        .then(response => response.json())
        .then(result => this.hello = result);
      }
    }
  }
}
</script>

<template>
  <input type="text" v-model="name">
  <button @click="refreshHello">Demander un bonjour !</button>
  <h1 v-show="!!hello">{{ hello }}</h1>
</template>
