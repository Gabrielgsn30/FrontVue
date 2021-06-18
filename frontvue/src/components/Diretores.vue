<template>
  <div>
    <h1>{{ msg }}</h1>
    <table>
      <thead>
        <tr>
          <th>
            id
          </th>
          <th>
            Nome
          </th>
          <th>
            Filmes
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="diretor in diretores" v-bind:key="diretor.id">
          <td>
            {{diretor.id}}
          </td>
          <td>
            {{diretor.nome}}
          </td>
          <td>
            {{diretor.filmes}}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Diretores',
  props: {
    msg: String
  },
  data:() =>{
    return{
    diretores:[],
  }
  },
  methods: {
    lista: (scope) =>{
      axios.get(`https://localhost:5001/Diretor`).then((res)=>{
      console.log(res)
      scope.diretores = res.data
    })
  }
},

  created(){
    this.lista(this)
  }
  
}
</script>

