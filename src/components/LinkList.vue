<template>
  <div class="m-auto mt-6 p-2 bg-gray-100 w-1/2 rounded-lg shadow-lg border border-dark">
    <ul>
      <li v-for="link in links" :key="link._id">
        <a :href="link.shortUrl" target="__bulk" class="hover:text-blue-500">{{ link.shortUrl}}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "LinkList",
  props: ["links"]
};
</script>

<style></style>
