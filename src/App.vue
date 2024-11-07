<template>
  <v-app>
    <v-app-bar height="70" mobile-breakpoint="580" color="indigo" density="comfortable" scroll-behavior="inverted">
      <template v-slot:prepend>
        <v-app-bar-nav-icon variant="text" @click.prevent="isOpen = !isOpen"></v-app-bar-nav-icon>
      </template>
      <v-app-bar-title style="margin-inline-start: 10px" class="d-none d-sm-block">

        <!-- <v-img src="@/assets/logo.svg" contain width="50" height="50" position="center" /> -->
        <P>Vuetify PWA</P>

        <!--  <span class="font-weight-black">ReportRID</span> -->
      </v-app-bar-title>
      <v-spacer></v-spacer>

      <template v-slot:append>
        <v-list class="ma-0 mr-n3 bg-transparent">
          <v-list-item prepend-icon="mdi-briefcase">
            <template v-slot:prepend>
              <v-avatar color="grey-lighten-4">
                <v-icon icon="mdi-account-circle" color="teal"></v-icon>
              </v-avatar>
            </template>
            <div class="d-flex align-center">
              <div>
                <v-list-item-title class="text-white">andyvega</v-list-item-title>
                <v-list-item-subtitle>andyvega@upe.edu.pe</v-list-item-subtitle>
              </div>
              <v-btn icon class="ml-2">
                <v-tooltip activator="parent" location="bottom">
                  Cerrar sesión
                </v-tooltip>
                <v-icon icon="mdi-logout"></v-icon>
              </v-btn>
            </div>
          </v-list-item>
        </v-list>
      </template>
    </v-app-bar>

    <!-- Navigation drawer -->
    <v-navigation-drawer v-if="mobile" v-model="isOpen">
      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
        <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
        <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
      </v-list>
      <template v-slot:append>
        <div class="pa-2">
          <v-btn block color="pink" class="text-none" variant="tonal" prepend-icon="mdi-logout">
            Cerrar sesión
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-navigation-drawer v-else :rail="isOpen" permanent floating>
      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
        <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
        <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- Main content -->
    <v-main>
      <v-container class="fill-height" fluid>
        <!--  <router-view /> -->

        <v-responsive class="align-centerfill-height mx-auto" max-width="auto">
          <v-img class="mb-4" height="150" src="@/assets/logo.png" />

          <div class="text-center">

            <h1 class="text-h2 font-weight-bold">Vuetify PWA</h1>
          </div>

          <div class="py-4" />


        </v-responsive>

      </v-container>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useDisplay } from 'vuetify'
const { mobile } = useDisplay()
const isOpen = ref(false)

</script>

<style scoped></style>
