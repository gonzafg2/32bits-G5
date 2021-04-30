<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h1 class="display-3 my-5">Busqueda de Juegos</h1>
          <h2 class="mb-5">Cantidad de Juegos Totales: {{ cantidadJuegos }}</h2>
        </div>
      </div>
      <div class="row">
        <div class="col-4 ms-auto">
          <label class="form-label">Filtro</label>
          <input type="text" class="form-control" v-model="filtro" />
        </div>
      </div>
      <div class="row">
        <div class="col-12" v-if="juegos">
          <TablaJuegos :productos="juegos" />
        </div>
        <div class="col-12" v-else>
          <h2>No es posible traer los juegos</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TablaJuegos from "@/components/TablaJuegos.vue";
import { mapState, mapGetters, mapMutations } from "vuex";

export default {
  name: "Busquedas",
  components: {
    TablaJuegos,
  },
  data() {
    return {
      // filtro: "",
    };
  },
  computed: {
    ...mapState(["juegos", "filtroCodigo"]),
    ...mapGetters(["cantidadJuegos"]),
    filtro: {
      get: function () {
        return this.filtroCodigo;
      },
      set: function (v) {
        this.añadirPalabra(v);
      },
    },
  },
  methods: {
    ...mapMutations(["añadirPalabra"]),
  },
};
</script>
