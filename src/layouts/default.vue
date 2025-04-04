<script setup>
//
</script>

<template>
  <div class="main">
    <v-main>
      <router-view />
    </v-main>

    <AppFooter />
  </div>
</template>

<style lang="scss" scoped>
.main {
  width: 100%;
  height: 100dvh;
  margin: 0 auto;
  display: flex;
  flex-direction: column;

  overflow-x: hidden;
}
</style>
