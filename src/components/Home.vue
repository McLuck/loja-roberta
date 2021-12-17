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
        <v-form>
          <v-row>
            <v-col cols='12' md='4'>
              <v-text-field v-model='nome' label='Name' required></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='sexo' label='Sexo' required></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='email' label='E-mail' required></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='endereco' label='Endereço (rua / avenida / numero)' required></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='bairro' label='Bairro' required></v-text-field>
            </v-col>
            <v-col cols='12' md='4'>
              <v-text-field v-model='cidade' label='Cidade' required></v-text-field>
            </v-col><v-col cols='12' md='4'>
              <v-text-field v-model='cep' label='CEP' required></v-text-field>
            </v-col>
            <v-col>
              <v-btn
                elevation="2"
                outlined @click="minhaFuncao"
              >BOTÃO</v-btn>
            </v-col>
          </v-row>
        </v-form>
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
  data () {
    return {
      nome: 'Alice',
      sexo: 'Feminino',
      email: 'roberta77@gmail.com',
      endereco: 'Av. A, num:102, casa 7',
      bairro: 'Bosque do Caju',
      cidade: 'Araraquara',
      cep: '13569-254'
    }
  },
  methods: {
    minhaFuncao () {
      // const msn = 'O nome da pessoa é : ' + this.nome + ' e o sexo é : ' + this.sexo
      const msg = `O nome é : ${this.nome} ; \n sexo : ${this.sexo} ; \n email : ${this.email} ;\n endereço: ${this.endereco} ; \n bairro : ${this.bairro} ; \n cidade : ${this.cidade} ; \n CEP : ${this.cep} .`
      alert(msg)
    }
  }
}
</script>

<style>
</style>
