<template>
  <div id="app">
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">SW Helper</router-link>

        <a
          role="button"
          class="navbar-burger burger"
          aria-label="menu"
          aria-expanded="false"
          data-target="mainNav"
        >
          <span aria-hidden="true"></span> <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div id="mainNav" class="navbar-menu">
        <div class="navbar-end">
          <router-link to="/" class="navbar-item" active-class="is-active">Home</router-link>
          <router-link to="/about" class="navbar-item" active-class="is-active">About</router-link>
        </div>
      </div>
    </nav>
    <div class="container"><router-view /></div>
    <footer class="footer">
      <div class="content has-text-centered">
        <p>
          <strong>SW Helper</strong> por Maxsuel Maccari. O código é licenciado
          sobre
          <a href="http://opensource.org/licenses/mit-license.php">MIT</a>. O
          código pode ser acessado através do nosso
          <a href="#">repositório no Github.</a>
        </p>
      </div>
    </footer>
  </div>
</template>

<style lang="scss"></style>
