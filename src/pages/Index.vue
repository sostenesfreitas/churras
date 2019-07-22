<template>
  <q-page class="flex flex-center t">
    <div class="bg-text flex column flex-center">
      <form @submit.prevent="simulateSubmit" class="q-pa-md">
        <h2>CHURRASCOMETRO</h2>
        <div class="flex row">
          <q-input
            color="white"
            v-model.number="qtdPessoa"
            type="number"
            label="Quantidade de Pessoas"
            rounded
            outlined
            dark
            style="width: 55%; margin-left: 5%;"
          />
          <q-toggle
            :false-value="true"
            :label="redModel ? 'Homem' : 'Mulher'"
            :true-value="false"
            color="pink"
            v-model="redModel"
          />
        </div>
        <div class="row justify-end">
          <q-btn
            :disable="!qtdPessoa"
            type="submit"
            :loading="submitting"
            label="Calcular"
            class="q-mt-md"
            color="white"
            dark
            outline
            rounded
          >
            <template v-slot:loading>
              <q-spinner-facebook />
            </template>
          </q-btn>
        </div>
      </form>
      <div class="flex column">
        <p v-show="qtd">Quantidade de carnes: {{qtd}} KG</p>
        <p v-show="qtdLata">Quantidade de Latas: {{qtdLata}} latas</p>
      </div>
    </div>
  </q-page>
</template>
<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      qtd: '',
      qtdLata: '',
      qtdPessoa: '',
      test: '',
      carneKgH: 500,
      carneKgM: 400,
      lataH: 8,
      lataM: 5,
      redModel: true,
      submitting: false
    }
  },

  methods: {
    simulateSubmit() {
      this.submitting = true
      setTimeout(() => {
        let q = parseInt(this.qtdPessoa)
        this.qtd = this.redModel
          ? q * (this.carneKgH / 1000)
          : q * (this.carneKgM / 1000)
        this.qtdLata = this.redModel ? q * this.lataH : q * this.lataM
        this.qtdPessoa = ''
        this.submitting = false
      }, 1000)
    }
  }
}
</script>
<style>
* {
  box-sizing: border-box;
}
.t {
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.5);
}
.bg-text {
  font-family: Arial, Helvetica, sans-serif;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.63);
  color: white;
  font-weight: bold;
  border: 1px solid #f1f1f1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  width: 55%;
  padding: 40px;
  text-align: center;
}
</style>
