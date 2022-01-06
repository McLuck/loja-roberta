<template>
  <div>
      <v-select :items= "items"></v-select>
      {{pessoas}}
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
           <th class="text-left">
            ID
          </th>
          <th class="text-left">
            Nome
          </th>
          <th class="text-left">
            E-Mail
          </th>
          <th class="text-left">
            Endereço
          </th>  <th class="text-left">
            Bairro
          </th>  <th class="text-left">
            Cidade
          </th>  <th class="text-left">
            Estado
          </th>
          </tr>
          </thead>
      <tbody>
        
        <tr v-for="variavel in pessoas" :key="variavel.id">
          <td>{{variavel.id}}</td>
          <td>{{variavel.nome}}</td>
          <td>{{variavel.email}}</td>
          <td>{{variavel.endereco.logradouro}}</td>
          <td>{{variavel.endereco.bairro}}</td>
          <td>{{variavel.endereco.cidade}}</td>
          <td>{{variavel.endereco.estado}}</td>
        </tr>
        <tr>
          <td> <v-btn color= red, @click="excluir()">Excluir</v-btn></td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
  <br>
  <br>
    <v-app-bar color="deep-purple accent-4" dense dark>
      <v-app-bar-nav-icon>
        <v-btn icon>
          <v-icon>mdi-car-connected</v-icon>
        </v-btn>
      </v-app-bar-nav-icon>
      <v-toolbar-title></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-account-circle</v-icon>
          </v-btn>
        </template>
         </v-menu>
      </v-app-bar>
      <v-main>
        <v-container>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="name"
      :counter="20"
      :rules="nameRules"
      label="Nome"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-text-field
      v-model="endereco.logradouro"
      :counter="20"
      :rules="endereco.enderecoRules"
      label="endereco"
      required
    ></v-text-field>

    <v-text-field
      v-model="endereco.bairro"
      :counter="20"
      :rules="endereco.bairroRules"
      label="Bairro"
      required
    ></v-text-field>

    <v-text-field
      v-model="endereco.cidade"
      :counter="20"
      :rules="endereco.cidadeRules"
      label="Cidade"
      required
    ></v-text-field>

    <v-text-field
      v-model="endereco.estado"
      :counter="10"
      :rules="endereco.estadoRules"
      label="Estado"
      required
    ></v-text-field>
    <v-btn
      :disabled="!valid"
      color= black,
      class="mr-4"
      @click="validate"
    >
      Salvar
    </v-btn>

    <v-btn
      color= black,
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>

    <v-btn
      color= red,
      @click="resetValidation"
    >
      Reset Validation
    </v-btn>
  </v-form>
  </v-container>
</v-main>
<br>
<br>
   <v-footer v:bind="fixed" padless>
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-footer>
  </div>
</template>

<script>
export default {
  data: () => ({
    pessoas: [],
    valid: true,
    name: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters'
    ],
    select: null,
    tabela: '',
    items: [
      '0 filhos',
      '1 filhos',
      '2 filhos',
      '3 filhos',
      '4 filhos',
      '5 filhos',
      '6 filhos',
      '7 filhos',
      '8 filhos',
      '9 filhos',
      '10 filhos'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ],
    endereco: {
      logradouro: null,
      endereco: null,
      enderecoRules: [
        v => !!v || 'Enderecço is required',
        v => (v && v.length <= 10) || 'Endereço must be valid'
      ],
      bairro: null,
      bairroRules: [
        v => !!v || 'Bairro is required',
        v => (v && v.length <= 10) || 'Bairro must be valid'
      ],
      cidade: null,
      cidadeRules: [
        v => !!v || 'Cidade is required',
        v => (v && v.length <= 10) || 'Cidade must be valid'
      ],
      estado: null,
      estadoRules: [
        v => !!v || 'Estado is required',
        v => (v && v.length <= 10) || 'Estado must be valid'
      ]
    }
  }),

  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        this.pessoas.push({
          id: new Date(),
          nome: this.name,
          email: this.email,
          endereco: {
            logradouro: this.endereco.logradouro,
            bairro: this.endereco.bairro,
            cidade: this.endereco.cidade,
            estado: this.endereco.estado
          }
        })
      }
    },
    excluir () {
   //this.pessoas.splice(id,1)
      console.log(this.pessoas.length)
      for (let i; i <= this.pessoas.length; i++){
        if (this.pessoas[i] === 2){
          console.log(this.pessoas[i])
        }
      }
      
      // this.pessoas.map((pessoa) => {
      //   let index = this.pessoas.filter(pessoa.nome, function () {
          
      //   } )
      //   if (index != -1){
      //     console.log(this.pessoas.splice(index,1))
      //   }
     //   console.log(this.pessoas.splice(index,1))
    //    console.log(index)
     //   console.log(this.pessoas[index].nome)
      //})


      // this.pessoas.filter( this.pessoas.nome, function (objeto,chave){
      //   return objeto.map( function (obj){
      //     return obj[chave]
      //   })
      
      // })
    },
    reset () {
      this.$refs.form.reset()
    },
    resetValidation () {
      this.$refs.form.resetValidation()
    }
  }
}
</script>

<style>
table,tr,td {
  border: steelblue
}
</style>
