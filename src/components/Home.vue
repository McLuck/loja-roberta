<template>
  <div>
      <v-select :items= "items"></v-select>
      {{pessoas}}
      pessoas
      <table >
        <tr>
          <td>
            nome
          </td>
          <td>
            email
          </td>
        </tr>
         <tr v-for= "variavel in pessoas" :key= "variavel.id">
          <td>
            {{variavel.nome}}
          </td>
          <td>
            {{variavel.email}}
          </td>
        </tr>
      </table>
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
      label="Name"
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
    items: [
      '0 filhos',
      '1 filhos',
      '2',
      '3',
      '4',
      '5',
      '6',
      '7',
      '8',
      '9',
      '10'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
    ],
    endereco: {
      logradouro: null,
      enderecoRules: [
        v => !!v || 'Enderecço is required',
        v => (v && v.length <= 10) || 'Endereço must be valid'
      ],
      bairroRules: [
        v => !!v || 'Bairro is required',
        v => (v && v.length <= 10) || 'Bairro must be valid'
      ],
      cidadeRules: [
        v => !!v || 'Cidade is required',
        v => (v && v.length <= 10) || 'Cidade must be valid'
      ],
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
            logradouro: this.endereco.logradouro
          }
        })
      }
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
  border: solid
}
</style>
