<template>
    <v-app>
      <v-main>
        <v-app-bar dark>
          <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
          <v-app-bar-title>Home</v-app-bar-title>
        </v-app-bar>
        <v-navigation-drawer
        v-model="drawer"
        absolute
        bottom
        temporary
        >
          <v-list
            nav
            dense
          >
            <v-list-item-group
              v-model="group"
              active-class="deep-purple--text text--accent-4"
            >
              <v-list-item>
                <v-list-item-title @click="goTo('/')">Home</v-list-item-title>
              </v-list-item>
  
              <v-list-item>
                <v-list-item-title @click="goTo('/cursos')">Cursos</v-list-item-title>
              </v-list-item>
  
              <v-list-item>
                <v-list-item-title @click="goTo('/users')">Usuários</v-list-item-title>
              </v-list-item>
  
              <v-list-item>
                <v-list-item-title @click="goTo('/calendario')">Cronograma</v-list-item-title>
              </v-list-item>
  
              <v-list-item>
                <v-list-item-title @click="goTo('/forum')">Fórum De Discussão</v-list-item-title>
              </v-list-item>
  
              <v-list-item>
                <v-list-item-title @click="goTo('/library')">Biblioteca Digital</v-list-item-title>
              </v-list-item>
              <div class="botaoLogoff">
                <v-btn dark @click="logout()">Logout</v-btn>
              </div>
            </v-list-item-group>
          </v-list>
        </v-navigation-drawer>
        <div class="boasVindas">
          <h1>Seja Bem-Vindo!</h1>
        </div>
      </v-main>
    </v-app>    
</template>

<script>
export default {
    data() {
        return {
            drawer: false,
            group: null,
        }
    },
    watch: {
        group () {
          this.drawer = false
        },
      },
    methods: {
        goTo(path) {
            this.$router.push(path)
        },
        logout(){
        if(confirm("Tem certeza que deseja sair?")){
          this.$store.dispatch('logout');
        }
      },
    }
}
</script>

<style>
.boasVindas{
  margin-top: 50px;
  margin-left: 50px;
}
</style>
