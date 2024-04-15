<template>
  <HeaderComponent/>
  <MainComponent/>
</template>

<script>
import { store } from './store.js';
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

  export default {
    name: 'App',
    components: {
      HeaderComponent,
      MainComponent
    },
    data() {
      return {
        store
      }
    },
    methods: {
      getCharacter() {
        // this.store.loading: true;
        axios.get(this.store.apiUrl + this.store.endPoint.characters).then((res) => {
          this.store.characters = res.data.results;
          this.store.total = res.data.info.count;
          console.log(res.data.info.count);
        }).catch((err) => {
          console.log(err);
        }).finally(() => {
          console.log('finally');
          // this.store.loading: false;
        })
      }
    },
    created() {
      this.getCharacter();
    }
  }
</script>

<style lang="scss" scoped>

</style>