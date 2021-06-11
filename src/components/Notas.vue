<template lang="html">
  <section class="src-components-notas">
      <vue-form :state="formState" @submit.prevent="enviar()">
        <h2 style="color:red">Notas</h2>
        <hr/>
        <validate tag="div">
          <label for="nombre">Nombre</label>
          <input 
            type="text" 
            id="nombre" 
            name="nombre" 
            class="form-control"
            autocomplete="off"
            v-model="formData.nombre"
            required
            :minlength="nombreLengthMin"
            :maxlength="nombreLengthMax"
            no-espacios
          >
          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>            
            <div slot="no-espacios" class="alert alert-danger mt-1">
              No se permiten espacios en ninguna parte de este campo
            </div>            
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo requiere como mínimo {{ nombreLengthMin }} caracteres
            </div>            
            <div v-if="formData.nombre.length == nombreLengthMax" class="alert alert-warning mt-1">
              Este campo debe tener como máximo {{ nombreLengthMax }} caracteres
            </div>            
          </field-messages>

        </validate>
        <br>

        <!-- campo apellido -->
        <validate tag="div">
          <label for="apellido">Apellido</label>
          <input 
            type="text" 
            id="apellido" 
            name="apellido" 
            class="form-control"
            autocomplete="off"
            v-model="formData.apellido"
            required
            :minlength="nombreLengthMin"
            :maxlength="nombreLengthMax"
            no-espacios
          >
          <field-messages name="apellido" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>            
            <div slot="no-espacios" class="alert alert-danger mt-1">
              No se permiten espacios en ninguna parte de este campo
            </div>            
            <div slot="minlength" class="alert alert-danger mt-1">
              Este campo requiere como mínimo {{ nombreLengthMin }} caracteres
            </div>            
            <div v-if="formData.apellido.length == nombreLengthMax" class="alert alert-warning mt-1">
              Este campo debe tener como máximo {{ nombreLengthMax }} caracteres
            </div>            
          </field-messages>

        </validate>
        <br>

        <!-- campo Nota -->
        <validate tag="div">
          <label for="nota">Nota</label>
          <input 
            type="number" 
            id="nota" 
            name="nota" 
            class="form-control"
            autocomplete="off"
            v-model.number="formData.nota"
            required
            :min="notaMin"
            :max="notaMax"
          >
          <!-- mensajes de validación -->
          <field-messages name="nota" show="$dirty">
            <div slot="required" class="alert alert-danger mt-1">Campo requerido</div>            
            <div slot="min" class="alert alert-danger mt-1">La nota mínima es {{notaMin}}</div>            
            <div slot="max" class="alert alert-danger mt-1">La nota máxima permitida es {{notaMax}}</div>            
          </field-messages>

        </validate>
        <br>

        <button class="btn btn-success my-3" :disabled="formState.$invalid" type="submit">Enviar</button>

      </vue-form>

      <hr>
      <div v-if="lofNota==0" class="alert alert-warning mt-1">
        No se encontraron notas
      </div>            

      <table class="table" v-else>
          <tr class="bg-success text-white">
              <th>ALUMNO</th>
              <th>Nota</th>
          </tr>
          <tr class="bg-dark" v-for="(nota,index) in notas" :key="index" :style="{'color':getColor(nota.nota)}">
              <td>{{ nota.nombre }} {{ nota.apellido }}</td>
              <td>{{ nota.nota }}</td>
          </tr>
          <tr class="bg-dark" :style="{'color':getColor(promedio)}">
              <td><strong>PROMEDIO:</strong></td>
              <td>{{ promedio }}</td>
          </tr>
      </table>

  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-notas',
    props: [],
    mounted () {

    },
    data () {
      return {
        formData : this.getInicialData(),
        formState : {},
        nombreLengthMin : 3,
        nombreLengthMax : 15,
        notaMin : 0,
        notaMax : 10,
        notas:[]
      }
    },
    methods: {
      getInicialData() {
        return {
          nombre: '',
          apellido: '',
          nota: ''
        }
      },
      enviar() {
        this.notas.push(this.formData)
        console.log(this.notas)
        this.formData = this.getInicialData()
        this.formState._reset()
      },
      getColor(nota) {
        let color = 'green';
        if (nota<=3) {
          color = 'red'
        } else if (nota>=4 && nota <=6) {
          color =  'yellow'
        }
        return color;
      }
    },
    computed: {
      lofNota() {
        return this.notas.length
      },
      promedio() {
        if (this.notas.length==0) return 0
        let total = this.notas.reduce((sum, it) => sum + it.nota, 0)
        let prom = total / this.notas.length
        return prom
      }
    }
}


</script>

<style scoped lang="css">
  .src-components-notas {
    margin: 2em;
  }
</style>
