<template>
  <div>
    <nav
      class="navbar header has-shadow"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand shadow">
        <a
          class="navbar-item"
          href="/"
        >
          <img
            src="~assets/comunal.svg"
            alt="Buefy"
            height="28"
          >
        </a>

        <div class="navbar-burger">
          <span />
          <span />
          <span />
        </div>
      </div>
      <div class="navbar-brand">
       <p>Mis problemas</p>

      </div>
    </nav>

    <section class="main-content columns">
      <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">
          General
        </p>
        <p>{{this.res}}</p>
        <!-- <ul class="menu-list">
          <li
            v-for="(item, key) of items"
            :key="key"
          >
            <nuxt-link
              :to="item.to"
              exact-active-class="is-active"
            >
              <b-icon :icon="item.icon" /> {{ item.title }}
            </nuxt-link>
          </li>
        </ul> -->
      </aside>

      <div class="container column is-10">
        <nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      res: null
    }
  },
  computed: {
    async getProblems() {
      const res = await this.$axios.$get('https://api-test.comunal.co/problem')
      this.res = res
      console.log(this.data);
    }
  }
}
</script>
<style>
  .navbar{
    display: flex;
    flex-direction: column;
  }

.shadow {
  box-shadow: 0 2px 0 0 whitesmoke;
}

p{
  font-size: 24px;
  font-family: "Montserrat";
}
</style>
