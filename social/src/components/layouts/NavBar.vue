<template>
  <nav :class="cor || 'blue'">
    <div class="nav-wrapper container">
      <!-- <a v-bind:href="url || '#'" class="brand-logo">{{ logo }}</a> -->
      <!-- <a :href="url || '#/'" class="brand-logo">{{ logo || 'Logo' }}</a> -->
      <router-link :to="url || '/'" class="brand-logo">{{ logo || 'Logo' }}</router-link>
      <ul id="nav-mobile" class="right hide-on-med-and-down">
        <slot />
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  props: ['logo', 'url', 'cor'],
  data() {
    return {};
  }
};
</script>

<style scoped>
</style>