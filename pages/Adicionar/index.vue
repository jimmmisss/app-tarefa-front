<template>
  <v-layout>
    <v-flex text-xs-center>

      <main>
       <v-container fluid fill-height class="loginOverlay">
          <v-layout flex align-center justify-center>
            <v-flex xs12 sm4 elevation-6>
              <v-toolbar class="pt-5 blue darken-1">
                <v-toolbar-title class="white--text">
                  <h4>Adicionar task</h4>
                </v-toolbar-title>
              </v-toolbar>
              <v-card>
                <v-card-text class="pt-4">
                  <div>
                      
                    <v-form ref="form" v-model="valid" lazy-validation>
                      
                      <v-text-field
                        v-model="titulo"
                        :rules="tituloRules"
                        :counter="60"
                        label="Título"
                        required
                      ></v-text-field>

                      <v-text-field
                        v-model="descricao"
                        label="Descrição"
                      ></v-text-field>
                     
                      <v-checkbox
                        v-model="checkbox"
                        :rules="[v => !!v || 'Precisa ativar status task']"
                        label="Status"
                        required
                      ></v-checkbox>

                      <v-btn
                        :disabled="!valid"
                        @click="submit"
                      >
                        submit
                      </v-btn>
                      <v-btn @click="clear">clear</v-btn>
                    </v-form>

                  </div>
                </v-card-text>
              </v-card>
            </v-flex>
          </v-layout>
       </v-container>
        
      </main>

    </v-flex>
  </v-layout>
</template>

<script>
  import axios from 'axios'

  export default {
    data: () => ({
      valid: true,
      titulo: '',
      descricao: '',

      tituloRules: [
        v => !!v || 'Título é obrigatório',
        v => (v && v.length <= 60) || 'Título deve ser menor ou igual a 10 caracteres'
      ],

      checkbox: false
    }),

    methods: {
      submit () {
        if (this.$refs.form.validate()) {
          axios.post('http://localhost:8080/v1/task', {
            headers: { 
              'Content-Type': 'application/json',
              'Access-Control-Allow-Origin': '*',
              'Accept': 'application/json, text/plain, */*',
              'Access-Control-Allow-Headers': 'Origin, Accept, Content-Type, Authorization, Access-Control-Allow-Origin'
            },
            title: this.titulo,
            description: this.descricao,
            status: this.checkbox
          })
        }
      },
      clear () {
        this.$refs.form.reset()
      }
    }

  }
</script>