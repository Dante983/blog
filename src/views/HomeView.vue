<template>
  <div class="home">
    Home
    <input type="text" v-model="search">
    <p>searched term - {{ search }}</p>
    <div v-for="name in matchinNames" :key="name">
      {{ name }}
    </div>
  </div>
</template>

<script>
import { computed, ref, watch, watchEffect } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const search = ref('')
    const names = ref(['nik', 'asdas', 'asd123', 'xcvzxc', 'ghjfgh', 'tyuyrt'])

    watch(search, () => {
      console.log('watcher');
    })

    watchEffect(() => {
      console.log('vacer');
    })

    const matchinNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return { names, search, matchinNames }
  },
  data() {
    return {
      score: 5
    }
  }
}
</script>
