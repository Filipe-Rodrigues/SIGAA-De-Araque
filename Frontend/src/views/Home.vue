<template>
  <div class="home">
    <v-container fluid class align-center>
      <h1 class="display-1 font-weight-light blue-grey--text text--darken-4 ml-3">Home</h1>
      <v-container class="mb-3">
        <v-layout row class="mb-1">
          <div
            class="title font-weight-regular text-capitalize grey--text text--darken-1"
          >Bem-vindo {{user.username}},</div>
        </v-layout>
        <v-layout row class="mb-2 pb-4">
          <div
            class="subheading font-weight-medium font-italic grey--text"
          >última vez logado: {{getLastLoginDate()}}</div>
        </v-layout>
        <v-layout row wrap justify-space-between>
          <v-flex sx12 sm6 md3>
            <DisplaySystemInfo
              :info="'Total de pesquisadores cadastrados'"
              :number="210"
              :icon_type="'person'"
            />
          </v-flex>
          <v-flex sx12 sm6 md3>
            <DisplaySystemInfo
              :info="'Total de grupos de pesquisa cadastrados'"
              :number="30"
              :icon_type="'group'"
            />
          </v-flex>
          <v-flex sx12 sm6 md3>
            <DisplaySystemInfo
              :info="'Total de projetos de pesquisa cadastrados'"
              :number="47"
              :icon_type="'find_in_page'"
            />
          </v-flex>
        </v-layout>
      </v-container>
      <v-divider></v-divider>
    </v-container>
  </div>
</template>

<script>
import DisplaySystemInfo from "../components/home/DisplaySystemInfo";
import moment from "moment";

export default {
  components: {
    DisplaySystemInfo
  },
  data() {
    return {
      //Last login in milliseconds
      user: { username: "Filipe Rodrigues", lastLogin: 1558037257662 },
      buttons: [{name: "Projetos", route: "/projects"},
                {name: "Grupos de Pesquisa", route: "/research-groups"},
                {name: "Pesquisadores", route: "/researches"},
                {name: "Disciplinas", route: "/disciplines"},
                {name: "Publicações", route: "/publications"},
                {name: "Perfil", route: "/profile/edit"}]
    };
  },
  methods: {
    getLastLoginDate() {
    /** Método utilizado para formatar millisegundos, do último tempo de 
     *  login do usuário armazenado, para a string dia/mes/ano
     *   @returns{string} string que apresenta a data do último login em DD/MM/YYYY
     */ 

      return moment(this.user.lastLogin).format("DD/MM/YYYY");
    }
  }
};
</script>

<style>
</style>
