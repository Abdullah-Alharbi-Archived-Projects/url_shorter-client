<template>
  <div id="app" class="text-center">
    <h1 class="text-blue-500 text-4xl">Create short links</h1>
    <h2 class="text-gray-500 font-semibold text-2xl">In One Click</h2>

    <LinkForm v-on:add-link="addLink" />

    <h1 class="text-gray-600 text-4xl p-0 m-0">My Links</h1>
    <hr class="border border-gray-400 w-48 p-0" />
    <LinkList :links="links" />
  </div>
</template>

<script>
import LinkList from "./components/LinkList";
import LinkForm from "./components/LinkForm";
import axios from "axios";

export default {
  name: "app",
  components: { LinkList, LinkForm },
  data() {
    return {
      links: []
    };
  },
  methods: {
    async addLink(longUrl) {
      // send request
      const {
        data: { url: link }
      } = await axios.post("http://localhost:8001/api/url/shorten", {
        longUrl
      });
      this.links = [...this.links, link];
    }
  },
  async created() {
    // get links
    const {
      data: { urls: links }
    } = await axios.get("http://localhost:8001/api/url/");
    this.links = [...links];
  }
};
</script>

<style src="./assets/css/tailwind.css">
</style>
