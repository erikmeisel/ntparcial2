<template lang="html">

  <section class="src-components-nav-bar">
    <nav class="navbar navbar-expand-md navbar-dark bg-info">
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div
        class="collapse navbar-collapse "
        id="navbarNav"
      >
        <ul class="navbar-nav nav-pills">
          <li class="nav-item">
            <router-link to="/">
              <a class="nav-link text-white mr-1" href="#">Inicio</a>
            </router-link>
          </li>

          <li class="nav-item">
            <router-link to="/notas">
              <a class="nav-link text-white mr-1" href="#"
                >Notas</a
              >
            </router-link>
          </li>

          <li class="nav-item">
            <router-link to="/respuestas">
              <a class="nav-link text-white mr-1" href="#"
                >Respuestas</a
              >
            </router-link>
          </li>
        </ul>
      </div>
    </nav>
    <!-- NavBar -->
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-nav-bar',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-nav-bar {

  }
</style>
