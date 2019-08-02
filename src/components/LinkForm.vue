<template>
  <form class="my-5" @submit="addLink" method="POST">
    <input
      type="text"
      placeholder="Link"
      name="longUrl"
      class="text-center bg-gray-200 focus:outline-none w-64 p-2 border border-gray-200 focus:border-blue-400 rounded-lg"
      v-model="longUrl"
    />
    <br />
    <button
      class="my-4 px-8 py-2 text-lg bg-blue-500 shadow-lg text-white rounded-lg shadow-lg hover:bg-blue-700"
    >Save</button>
  </form>
</template>

<script>
export default {
  name: "LinkForm",
  data() {
    return {
      longUrl: ""
    };
  },
  methods: {
    addLink(e) {
      e.preventDefault();

      const longUrl = this.longUrl;

      this.$emit("add-link", longUrl);
      this.longUrl = "";
    }
  }
};
</script>

<style></style>
