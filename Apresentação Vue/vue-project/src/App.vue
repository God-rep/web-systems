<script setup>
import { ref } from 'vue'
const matricula = ref('')
const senha = ref('')
const isLoginVisible = ref(true)
const testLogin = ref(false)



const matriculaArray = [
                        {"Nome": "Marcelo", "Matricula": 1, "Senha": 1234},
                        {"Nome": "Jason", "Matricula": 2, "Senha": 4321}
                       ]

function searchLogin(matricula, senha){

  testLogin.value = matriculaArray.some(
        user => user.Matricula === matricula.value && user.Senha === senha.value)

  if (testLogin.value) isLoginVisible.value = false

  return testLogin.value
}

</script>

<template>
  <head>
  </head>
  <body>
    <div id="listas-laterais">
      <div id="lista-esquerda" class="lista-lateral">
        <div class="titulo-lista-lateral">
          <h2> Informes </h2>
        </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
      </div>
      <div id="lista-direita" class="lista-lateral" v-if="testLogin">
        <div class="titulo-lista-lateral">
          <h2> Artigos </h2>
        </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
        <div class="item-lista-lateral"> </div>
      </div>
    </div>
    <div id="login" v-if="isLoginVisible">
      <img id="logo" src="https://img.freepik.com/vetores-gratis/design-de-logotipo-do-ensino-medio-desenhado-a-mao_23-2149667303.jpg?semt=ais_hybrid&w=740">
      <input id="caixa-matricula" v-model="matricula"></input>
      <input id="caixa-senha" v-model="senha"></input>
      <button id="botao-envia" @click="searchLogin(matricula, senha),
              matricula = '', senha = '', testLogin = true, isLoginVisible = false"> Enviar </button>
    </div>
    <div id="principal" v-else v-if="testLogin">
    </div>
  </body>
  <footer>
  </footer>

</template>

<style>
body{
  background-color: white;

}
#login{
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  top: 500px;
}

#logo{
  position:absolute;
  bottom: 100px;
  width: 300px;

}

#caixa-matricula{
  position: relative;
  border-color: #0C86C9;
  border-width: 3px;
}
#caixa-senha{
  position: relative;
  border-color: #0C86C9;
  border-width: 3px;
}
#botao-envia{
  position: relative;
  left: 120px;
  bottom: 33px;
}

#principal{
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#listas-laterais{
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between

}

.lista-lateral{
  position: absolute;
  display:flex;
  flex-direction: column;
  align-items: center;
  background-color: #F37032;
  width: 250px;
  height: 475px;
  top: 125px;
  border-radius: 0px 0px 10px 10px;
}

#lista-esquerda{
  left: 0;
}

#lista-direita{
  right: 0;
}

.titulo-lista-lateral{
  position:relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 10px;
  width: 90%;
  height: 70px;
  background-color: white;

  & h2{
    position: absolute;
    color: #0C86C9;
  }

}

.item-lista-lateral{
  position: relative;
  margin-top: 4px;
  width: 90%;
  height: 50px;

  background-color: white;

}

</style>