<template>
  <section class="content" v-if="topic">
    <router-link to="/">Voltar</router-link>
    <h1>{{ topic.title }}</h1>
    <div class="tags">
      <span class="tag" v-for="tag in topic.tags" :key="tag">{{ tag }}</span>
    </div>
    <p>{{ topic.description }}</p>

    <hr />

    <div v-html="content"></div>

    <hr />
    <router-link to="/">Voltar</router-link>
  </section>
</template>

<script>
import topics from "../topics";
import marked from "marked";

export default {
  data() {
    return {
      topic: null
    };
  },
  computed: {
    content() {
      console.log(this.topic.content);
      return marked(this.topic.content, { sanitize: true });
    }
  },
  mounted() {
    this.topic = topics.find(topic => topic.id == this.$route.params.id);
  }
};
</script>

<style></style>
