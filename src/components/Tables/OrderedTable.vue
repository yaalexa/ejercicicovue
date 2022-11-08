<template>
  <div>
    <b-table id="tabla" :fields="encabezado" :items="categoria" responsive="sm"/>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "ordered-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      categoria: [],
      encabezado: [
        { key: "id", label: "Id" },
        { key: "nombre", label: "Nombre" },
        { key: "descripcion", label: "Descripcion" },
      ],
    };
  },
  mounted() {
    this.getcategorias();
  },
  methods:{

getcategorias(){
    axios.get("http://127.0.0.1:8000/api/categoria").then((response)=>
    {
       this.categoria=response.data;
    })

},
NuevaCategoria(){
    this.$router.push('NuevaCategoria')
}


},
};
</script>
<style>
#tabla{
  
}
</style>
