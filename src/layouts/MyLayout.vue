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
      <q-scroll-area style="height: calc(100% - 200px); margin-top: 200px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item clickable tag="a" target="_blank" href="https://www.linkedin.com/in/paulo-arthur-haller-junior-65109815b/">
              <q-item-section avatar>
                <q-icon name="fab fa-linkedin" />
              </q-item-section>
              <q-item-section>
                <q-item-label>Linkedin</q-item-label>
                <q-item-label caption>linkedin.com</q-item-label>
              </q-item-section>
            </q-item>

            <q-item>
              <q-item-section avatar>
                <q-icon name="fab fa-whatsapp" />
              </q-item-section>
              <q-item-section>
                <q-item-label>Whatsapp</q-item-label>
                <q-item-label caption>(11) 94231-8033</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="statics/contabilidade2.jpg" style="height: 200px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="statics/myFoto.jpg">
            </q-avatar>
            <div class="text-weight-bold">Paulo Arthur</div>
            <div>@pah_junior</div>
          </div>
        </q-img>
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
