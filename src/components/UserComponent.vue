<script>
export default {
  name: "HomeView",
  props: ["displayName", "img", "followers"],
};
</script>

<template>
  <h1>Hola {{ displayName }}</h1>
  <img :src="img" />
  <h2>Seguidores: {{ followers }}</h2>
</template>
