<template>
  <section class="section">
    <section class="hero">
      <div class="hero-body">
        <h1 class="title">Bem vindo ao SW Helper</h1>
        <p class="subtitle">Em que você precisa de ajuda?</p>
        <input v-model="search" class="input" type="text" placeholder="Eu quero...">
      </div>
    </section>

    <div v-for="topic in filtered" :key="topic.id" class="card">
      <a href="#">
        <div class="card-content">
          <p class="title">{{ topic.title }}</p>
          <div class="content">{{ topic.description }}</div>
        </div>
      </a>
    </div>
  </section>
</template>

<script>
export default {
  name: "home",
  data () {
    return {
      search: "",
      topics: [
        {
          id: 1,
          title: 'Registrar um domínio',
          description: 'Está com dificuldades em registrar o seu domínio .co? Nós vamos te ajudar!',
          tags: [
            'site',
            'registro',
            'website'
          ]
        },
        {
          id: 2,
          title: 'Criar um questionário',
          description: 'Precisa criar um questionário para fazer pesquisas de mercado? Veio ao lugar certo.',
          tags: [
            'entrevista',
            'perguntas',
            'pesquisa',
            'mercado'
          ]
        },
        {
          id: 3,
          title: 'Criar uma landing page',
          description: 'Quer criar uma landing page e não sabe por onde começar? Esse é o guia.',
          tags: [
            'website',
            'desenvolver',
            'pagina'
          ]
        },
        {
          id: 4,
          title: 'Prototipar um app',
          description: 'Quer desenvolver seu app e está perdido? Vamos começar pelo protótipo.',
          tags: [
            'app',
            'aplicativo',
            'celular',
            'desenvolver',
            'criar',
            'fazer'
          ]
        },
        {
          id: 5,
          title: 'Criar um business model canvas',
          description: 'Quer mais dicas e ferramentas que te ajude a criar o seu canvas de negócios? Veio ao lugar certo!',
          tags: [
            'modelo',
            'negocios',
            'canvas',
            'fazer'
          ]
        }
      ]
    }
  },
  computed: {
    filtered () {
      return this.topics.filter(topic => {
        return topic.title.toLowerCase().includes(this.search.toLowerCase()) ||
          topic.tags.some(tag => {
            let terms = this.search.toLowerCase().split(' ')
            return terms.some(term => tag.toLowerCase().includes(term))
          })
      })
    }
  }
};
</script>
