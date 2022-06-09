<template>
  <div class="container-sm">
    <form @submit.prevent="verificar()">
      <div class="mb-3">
        <label for="nombre" class="form-label">Nombre</label>
        <input type="text" class="form-control" id="nombre" />
      </div>
      <div class="mb-3">
        <label for="monto" class="form-label">Monto a invertir</label>
        <input type="number" min="1000" class="form-control" id="monto" />
      </div>
      <div class="mb-3">
        <label for="dias" class="form-label">Cantidad de dias</label>
        <input type="number" min="30" class="form-control" id="dias" />
      </div>
      <div class="mb-3 form-check">
        <input
          v-model="formulario.reinvertir"
          type="checkbox"
          class="form-check-input"
          id="reinvertir"
        />
        <label class="form-check-label" for="reinvertir">Check me out</label>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <Error v-show="!formulario.verificado" :msg="formulario.mensaje" />
  </div>
</template>

<script>
import Error from "@/components/Error.vue";

export default {
  name: "FormularioComponente",
  components: {
    Error,
  },
  data() {
    return {
      formulario: {
        nombre: "",
        monto: 0,
        dias: 0,
        reinvertir: false,
        mensaje: "",
        verificado: true,
      },
    };
  },
  methods: {
    verificar() {
      while (this.formulario.nombre === "") {
        this.formulario.mensaje = "Falta el nombre";
        this.formulario.verificado = false;
      }
      while (this.formulario.monto < 1000 || this.formulario.monto == "") {
        this.formulario.mensaje = "El monto debe ser mayor o igual a 1000";
        this.formulario.verificado = false;
      }
      while (this.formulario.dias < 30 || this.formulario.dias == "") {
        this.formulario.mensaje =
          "La cantidad de dias debe ser mayor o igual a 30";
        this.formulario.verificado = false;
      }

      //Validacion correcta
    },
  },
};
</script>
