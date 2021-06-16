
<template>
  <v-app id="inspire">
   <v-navigation-drawer
    v-model="drawer" app
   >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            My To Do List
          </v-list-item-title>
          <v-list-item-subtitle>
            Final CS 260
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>


   <v-app-bar
        app
        color="primary"
        dark
        src="https://picsum.photos/1920/1080?random"
        height="170"
      >
        <template v-slot:img="{ props }">
          <v-img
            v-bind="props"
            gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
          ></v-img>


      
        </template>

      
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>My To Do List</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon id="no-background-hover" to="/">
          <v-icon>mdi-home</v-icon>
        </v-btn>
  
        <v-btn icon id="no-background-hover" to="/dashboard">
          <v-icon>mdi-account</v-icon>
        </v-btn>


    
     <v-spacer></v-spacer>
      Stick Together
      </v-app-bar>
      
    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>
  <div>
  <div class="fluid-container footer">
    <p class="text-center">Copyright 2018, ABC Marketing. All Rights Reserved.</p>
  </div>
</div>

  </v-app>
  
</template>

<script>
import Snackbar from './components/Shared/Snackbar.vue'
  export default {
    data: () => ({ 
      drawer: null,
        items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to: '/about' },
        ],
      }),
      mounted() {
        this.$store.dispatch('getTasks')
      },
    components: {
      'snackbar': require('@/components/Shared/Snackbar.vue').default
    }
  }
</script>

<style>
  .fluid-container.footer{
    height: 30px;
  background: rgb(181, 216, 236);
}
.fluid-container.footer > *:last-child {
    margin-bottom: 0px;
    color: black;
  }
</style>