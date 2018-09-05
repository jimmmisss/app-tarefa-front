<template>
  <div>

    <v-flex xs12>
      <v-card v-for="item in tasks" style="margin: 20px">

        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">{{ item.title }}</h3>
            <div>{{ item.description }}</div>
          </div>
        </v-card-title>

        <v-card-actions>
          <v-btn flat color="orange">Editar</v-btn>
          <v-btn @click.stop.prevent="excluir(item.id)" flat color="orange">excluir</v-btn>
        </v-card-actions>

      </v-card>
    </v-flex>
      
  </div>  
  
</template>

<script>
import axios from 'axios'

  export default {
    
    data: () => ({
      tasks:{},
      dialog: false
    }),

    mounted() {
      axios.get('http://localhost:8080/v1/tasks').then((response) => {
        this.tasks = response.data
        console.log(response.data)
      })
    },

    
    methods: {
      excluir: function(id) {
        axios.delete('http://localhost:8080/v1/task/' + id).then(response => {
          console.log(this.result);
      })
      }
    }


  }
</script>