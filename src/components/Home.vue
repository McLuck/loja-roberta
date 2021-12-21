<template>
  <div>
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

        <v-list>
          <v-list-item v-for="n in 5" :key="n" @click="() => {}">
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main>
      conteudo {{ nome }} {{ sexo }} {{email}}{{ endereco }} {{ bairro }} {{ cidade }} {{ cep }} <br />
      <br/>
      <input type='text' v-model='nome' />
      <br/>
       <input type='text' v-model='filhos' />
      <br/>
      <input type='text' v-model='sexo' />
      <br/>
      <input type='text' v-model='email' />
      <br/>
      <input type='text' v-model='endereco' />
      <br/>
      <input type='text' v-model='bairro' />
      <br/>
      <input type='text' v-model='cidade' />
      <br/>
      <input type='text' v-model='cep' />
      <v-container>
        <form @submit = "checkForm" action="https://vuejs.org/" method="post">
        <p v-if = "errors.length">
          <b>Por favor, corrija o(s) seguinte(s) erro(s):</b>
          <ul>
            <li v-for= "error in errors" v-bind:key= "error">{{ error }}</li>
          </ul>
          </p>
          <v-row>
            <v-col cols='12' md='4'>
              <v-text-field v-model='nome' label='Name' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='filhos' label='Filhos' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='sexo' label='Sexo' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='email' label='E-mail' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='endereco' label='Endereço (rua / avenida / numero)' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='bairro' label='Bairro' ></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='cidade' label='Cidade' ></v-text-field>
            </v-col><v-col cols='12' md='4'>
              <v-text-field v-model='cep' label='CEP' ></v-text-field>
            </v-col>
            <v-col>
              <v-btn
                elevation="2"
                outlined type= "submit" >BOTÃO</v-btn>
            </v-col>
          </v-row>
        </form>
      </v-container>
    </v-main>
    <v-footer v:bind='fixed' padless>
      <v-col class='text-center' cols='12'>
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-footer>
  </div>
</template>

<script>
export default {
  el: '#Home',
  data () {
    return {
      errors: [],
      nome: null,
      filhos: null,
      sexo: null,
      email: null,
      endereco: null,
      bairro: null,
      cidade: null,
      cep: null
    }
  },
  methods: {
    minhaFuncao () {
      // https://br.vuejs.org/v2/cookbook/form-validation.html
      // const msn = 'O nome da pessoa é : ' + this.nome + ' e o sexo é : ' + this.sexo
      const msg = `O nome é : ${this.nome}  \n e seus filhos(a) são:  ${this.filhos} \n sexo : ${this.sexo}  \n email : ${this.email} \n endereço: ${this.endereco} \n bairro : ${this.bairro} \n cidade : ${this.cidade} \n CEP : ${this.cep} `
      alert(msg)
    },
    checkForm: function (e) {
      if (this.nome && this.filhos && this.sexo && this.email && this.endereco && this.bairro && this.cidade && this.cep) {
        return true
      }
      this.errors = []
      if (!this.nome) {
        this.errors.push('o nome é obrigatório')
      }
      if (!this.nome) {
        this.errors.push('o nome é obrigatório')
      }
      if (!this.filhos) {
        this.errors.push('o nome dos filhos é obrigatório')
      }
      if (!this.sexo) {
        this.errors.push('o sexo é obrigatório')
      }
      if (!this.email) {
        this.errors.push('o e-mail é obrigatório')
      }
      if (!this.endereco) {
        this.errors.push('o endereço é obrigatório')
      }
      if (!this.bairro) {
        this.errors.push('o bairro é obrigatório')
      }
      if (!this.cidade) {
        this.errors.push('a cidade é obrigatório')
      }
      if (!this.cep) {
        this.errors.push('o cep é obrigatório')
      }
      e.preventDefault()
    }
  }
}
</script>

<style>
</style>
