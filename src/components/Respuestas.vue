<template lang="html">

  <section class="src-components-respuestas">
    <h1>Respuestas</h1>
    <table class="table">
          <tr class="text-bold">
              <th>Numero Pregunta</th>
              <th>Respuesta</th>
          </tr>
          <tr v-for="(respuesta,index) in preguntas" :key="index">
              <td>{{ respuesta.numero }}</td>
              <td>{{ respuesta.respuestas }}</td>
          </tr>
      </table>    
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-respuestas',
    props: [],
    mounted () {

    },
    data () {
      return {
        preguntas : [
            { numero: 1, respuestas: ['c'] },
            { numero: 2, respuestas: ['c'] },
            { numero: 3, respuestas: ['b'] },
        ]
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-respuestas {

  }
</style>
