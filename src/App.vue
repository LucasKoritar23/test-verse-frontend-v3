<template>
  <div id="app">
    <div id="nav">
      <HeaderComponent class="mb-5" />
    </div>
    <router-view />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';

export default {
  components: {
    HeaderComponent,
  },
}
</script>