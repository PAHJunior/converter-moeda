<template>
  <q-page  >
    <!-- <img alt="Quasar logo" src="~assets/logo-contabilidade.png"> -->

    <div class="row justify-center q-pa-md">
      <div class="row col-12">
        <q-card class="col-12 ">
          <q-card-section>
            <q-input
              outlined
              v-model="text"
              dense
              label="Quantidade"
            />
          </q-card-section>
        </q-card>

        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>De:</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
             <q-avatar rounded  size="80px">
              <img src="~assets/bra.png">
            </q-avatar>
            Real Brasil, BRL
          </q-card-section>
        </q-card>

        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>Para:</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
             <q-avatar rounded  size="80px">
              <img src="~assets/bra.png">
            </q-avatar>
            Real Brasil, BRL
          </q-card-section>
        </q-card>
        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>Resultado</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
             {{ resultado }}
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex'
}
</script>
