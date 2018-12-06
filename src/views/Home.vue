<template>
  <section class="section">
    <section class="hero">
      <div class="hero-body">
        <h1 class="title">Bem vindo ao SW Helper</h1>
        <p class="subtitle">Em que você precisa de ajuda?</p>
        <input
          v-model="search"
          class="input"
          type="text"
          placeholder="Eu quero..."
        />
      </div>
    </section>

    <div v-for="topic in filtered" :key="topic.id" class="card">
      <router-link :to="{ name: 'topic', params: { id: topic.id } }">
        <div class="card-content">
          <p class="title">{{ topic.title }}</p>
          <div class="content">{{ topic.description }}</div>
          <div class="tags">
            <span class="tag" v-for="tag in topic.tags" :key="tag">{{
              tag
            }}</span>
          </div>
        </div>
      </router-link>
    </div>
  </section>
</template>

<script>
import topics from "../topics";

export default {
  name: "home",
  data() {
    return {
      search: "",
      topics: topics
    };
  },
  computed: {
    filtered() {
      return this.topics.filter(topic => {
        return (
          topic.title.toLowerCase().includes(this.search.toLowerCase()) ||
          topic.tags.some(tag => {
            let terms = this.search.toLowerCase().split(" ");
            return terms.some(term => tag.toLowerCase().includes(term));
          })
        );
      });
    }
  }
};
</script>
