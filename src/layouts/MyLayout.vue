<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>
          Converter Moeda
        </q-toolbar-title>

        <div>v{{ versao }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-2"
    >
      <q-list>
        <q-item-label class="text-center" header>ETEC de Embu</q-item-label>

        <q-item clickable>
          <q-item-section avatar>
            <q-icon name="fas fa-donate" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Configuração de valores</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable tag="a" target="_blank" href="https://www.linkedin.com/in/paulo-arthur-haller-junior-65109815b/">
          <q-item-section avatar>
            <q-icon name="fab fa-linkedin" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Linkedin</q-item-label>
            <q-item-label caption>linkedin.com</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      versao: process.env.VERSAO,
      leftDrawerOpen: false
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
</style>
