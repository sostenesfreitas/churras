<template>
  <q-layout view="lHh Lpr lFf" class="back">
    <q-header elevated></q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MyLayout",
  data() {
    return {};
  }
};
</script>

<style>
.back {
  background-size: auto;
  background: url("../assets/churra.jpg");
  height: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
