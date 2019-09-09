<template>
  <q-page  >
    <!-- <img alt="Quasar logo" src="~assets/logo-contabilidade.png"> -->

    <div class="row justify-center q-pa-md">
      <div class="row col-12">
        <q-card class="col-12 ">
          <q-card-section>
            <q-input
              ref="quantidade"
              type="number"
              outlined
              dense
              v-model="quantidade"
              hint="Valor a ser convertido"
              lazy-rules
              :rules="[ val => val.length > 0 || 'O valor deve ser maior que 0']"
            />
          </q-card-section>
        </q-card>

        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>De:</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
            <div class="row items-baseline">
            <!-- Real Brasil, BRL -->
              <q-card class="col-3 no-border no-shadow">
                <q-avatar class="absolute-center">
                  <img :src="de.img">
                </q-avatar>
              </q-card>

              <q-card class="col-9 no-shadow">
                <q-select
                  :error="this.de == this.para"
                  :hint="'R$ ' + de.valor"
                  outlined
                  v-model="de"
                  :options="options"
                  color="primary"
                  dense
                  options-selected-class="text-deep-primary"
                >
                  <template v-slot:error>
                    Por favor, selecione tipos de moedas diferentes
                  </template>
                  <template v-slot:option="scope">
                    <q-item
                      v-bind:imagem_de="scope.opt.icon"
                      v-bind="scope.itemProps"
                      v-on="scope.itemEvents"
                    >
                      <q-item-section avatar>
                        <q-icon :name="scope.opt.icon" />
                      </q-item-section>
                      <q-item-section>
                        <q-item-label v-html="scope.opt.label" />
                        <q-item-label caption>{{ scope.opt.description }}</q-item-label>
                      </q-item-section>
                    </q-item>
                  </template>
                </q-select>
              </q-card>
            </div>
          </q-card-section>
        </q-card>

        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>Para:</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
            <div class="row items-baseline">
            <!-- Real Brasil, BRL -->
              <q-card class="col-3 no-border no-shadow">
                <q-avatar class="absolute-center">
                  <img :src="para.img">
                </q-avatar>
              </q-card>

              <q-card class="col-9 no-shadow">
                <q-select
                  outlined
                  :error="this.de == this.para"
                  :hint="'R$ ' + para.valor"
                  v-model="para"
                  :options="options"
                  color="primary"
                  dense
                  options-selected-class="text-deep-primary"
                >
                  <template v-slot:error>
                    Por favor, selecione tipos de moedas diferentes
                  </template>
                  <template v-slot:option="scope">
                    <q-item
                      v-bind:imagem_de="scope.opt.icon"
                      v-bind="scope.itemProps"
                      v-on="scope.itemEvents"
                    >
                      <q-item-section avatar>
                        <q-icon :name="scope.opt.icon" />
                      </q-item-section>
                      <q-item-section>
                        <q-item-label v-html="scope.opt.label" />
                        <q-item-label caption>{{ scope.opt.description }}</q-item-label>
                      </q-item-section>
                    </q-item>
                  </template>
                </q-select>
              </q-card>
            </div>
          </q-card-section>
        </q-card>
        <q-card class="col-12">
          <q-toolbar class="bg-grey-4">
            <q-toolbar-title>Resultado:</q-toolbar-title>
          </q-toolbar>
          <q-card-section>
            <div class="row">
              <q-card class="col-9 no-shadow">
                {{ converterMoeda }}
              </q-card>
            </div>
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
  name: 'PageIndex',
  created () {
    this.de = this.options[0]
    this.para = this.options[1]
  },
  data () {
    return {
      quantidade: 0,
      qtd: 110,
      para: '',
      de: '',
      options: [
        {
          label: 'Real',
          value: 'real',
          valor: '1.00',
          icon: 'img:statics/moedas/real.png',
          img: 'statics/moedas/real.png'
        },
        {
          label: 'Biticon',
          value: 'biticon',
          valor: '38938.78',
          icon: 'img:statics/moedas/bitcoin.png',
          img: 'statics/moedas/bitcoin.png'
        },
        {
          label: 'Ethereum',
          value: 'ethereum',
          valor: '679.82',
          icon: 'img:statics/moedas/Ethereum.png',
          img: 'statics/moedas/Ethereum.png'
        },
        {
          label: 'Ripple',
          value: 'ripple',
          valor: '1.03',
          icon: 'img:statics/moedas/Ripple.png',
          img: 'statics/moedas/Ripple.png'
        },
        {
          label: 'Litecoin',
          value: 'litecoin',
          valor: '261.84',
          icon: 'img:statics/moedas/litecoin.png',
          img: 'statics/moedas/litecoin.png'
        },
        {
          label: 'Biance coin',
          value: 'biancecoin',
          valor: '85.86',
          icon: 'img:statics/moedas/biancecoin.png',
          img: 'statics/moedas/biancecoin.png'
        },
        {
          label: 'Stellar',
          value: 'stellar',
          valor: '0.25',
          icon: 'img:statics/moedas/Stellar.png',
          img: 'statics/moedas/Stellar.png'
        },
        {
          label: 'Monero',
          value: 'monero',
          valor: '265.83',
          icon: 'img:statics/moedas/Monero.png',
          img: 'statics/moedas/Monero.png'
        },
        {
          label: 'Dash',
          value: 'dash',
          valor: '318.77',
          icon: 'img:statics/moedas/Dash.png',
          img: 'statics/moedas/Dash.png'
        },
        {
          label: 'NEO',
          value: 'neo',
          valor: '34.69',
          icon: 'img:statics/moedas/Neo.png',
          img: 'statics/moedas/Neo.png'
        },
        {
          label: 'NEM',
          value: 'nem',
          valor: '0.19',
          icon: 'img:statics/moedas/Nem.png',
          img: 'statics/moedas/Nem.png'
        }
      ]
    }
  },
  methods: {
    myRule (val) {
      if (this.de === this.para) {
        return (!!val || '* Required')
      }
    },
    onSubmit () {
      console.log(this.$refs.name)
      this.$refs.name.validate()
    }
  },
  computed: {
    converterMoeda: function () {
      if (this.de.value === 'real') {
        let retorno = this.quantidade / this.para.valor
        return retorno.toFixed(6).replace('.', ',')
      } else {
        let valorReal = this.quantidade * this.de.valor
        let moeda = valorReal / this.para.valor
        return moeda.toFixed(6).replace('.', ',')
      }
    }
  }
}
</script>

<style>
input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
input[type=number] {
  -moz-appearance: textfield;
  appearance: textfield;
}
</style>
