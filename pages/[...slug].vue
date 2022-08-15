<template>
  <div>
    Catch all route
    <div>
      <NuxtLink to="/1">1</NuxtLink><br />
      <NuxtLink to="/2">2</NuxtLink><br />
      <NuxtLink to="/non-existing-page">404</NuxtLink>
      <button @click="refresh">Refresh data</button>
    </div>
    Data based on route {{ route.params.slug }}
    {{ data }}
  </div>
</template>
<script setup lang="ts">
const route = useRoute();

console.log(route.params.slug);
const { data, refresh } = await useFetch(
  'https://jsonplaceholder.typicode.com/posts/' + route.params.slug
);

//onMounted(() => {
//  refresh();
//});
</script>
