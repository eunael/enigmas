<script setup lang="ts">
import { ref, type Ref } from 'vue'

const darkModeOff: Ref<boolean> = ref(false)
const light: Ref<boolean> = ref(true)
const msg: Ref<string> = ref('')

function toggleLight() {
  light.value = !light.value
}

function tentarSenha() {
  msg.value = '( se está vendo esta mensagem, parabéns! vc não acertou a senha, mas calma é pq eu ainda não terminei o projeto. haverá mais em breve, então, até logo! )'

  setTimeout(() => {
    msg.value = ''
  }, 15000);
}
</script>

<template class="">
  <div class="h-screen flex flex-col" :class="{ 'bg-white': light, 'bg-black': !light }">
    <div class="px-4">WIP Enigmas... (fala rapaziada!)</div>
    <div class="text-sm text-gray-500 mb-5 w-fit px-4">
      <i>
        <strong>Aviso</strong>: não utilize o "Inspecionar" a página para resolver, pois isso é trapaça.
        <strong>explore</strong>
        a <strong class="underline">UI</strong> antes de tudo, ela vai te <strong class="cursor-pointer"
          @click="toggleLight" v-text="!light ? 'ocultar' : 'mostrar'"></strong> o que
        precisa para resolver.</i>
    </div>

    <div class="text-white w-full max-w-md mx-auto grow flex justify-center items-center border border-white mb-5">
      <form class="select-none" @submit.prevent="tentarSenha">
        <p class="text-black mb-5 text-2xl">Informe a senha:</p>
        <div class="flex gap-3 mb-5 w-fit mx-auto">
          <input
            type="number"
            class="bg-white text-black text-4xl px-2 w-12 [appearance:textfield] [&::-webkit-outer-spin-button]:appearance-none [&::-webkit-inner-spin-button]:appearance-none"
            required
            min="0"
            max="9"
          >
          <input
            type="number"
            class="bg-white text-black text-4xl px-2 w-12 [appearance:textfield] [&::-webkit-outer-spin-button]:appearance-none [&::-webkit-inner-spin-button]:appearance-none"
            required
            min="0"
            max="9"
          >
          <input
            type="number"
            class="bg-white text-black text-4xl px-2 w-12 [appearance:textfield] [&::-webkit-outer-spin-button]:appearance-none [&::-webkit-inner-spin-button]:appearance-none"
            required
            min="0"
            max="9"
          >
          <input
            type="number"
            class="bg-white text-black text-4xl px-2 w-12 [appearance:textfield] [&::-webkit-outer-spin-button]:appearance-none [&::-webkit-inner-spin-button]:appearance-none"
            required
            min="0"
            max="9"
          >
        </div>
        <div class="text-end mb-5 mx-auto w-fit">
          <button class="font-bold border border-white px-4 py-2 cursor-pointer" type="submit">Enviar</button>
        </div>
        <div>
          <p class="text-wrap text-center px-4" v-text="msg"></p>
        </div>
      </form>
    </div>

    <div class="text-center text-sm py-3" :class="{ 'text-white': !light, 'text-black': light }">
        2025&copy;, Feito por <a href="https://github.com/eunael" class="link text-blue-500"
            target="_blank">eunael</a>.
    </div>

    <Transition name="fade">
      <div
        v-if="!darkModeOff"
        class="bg-black text-gray-50 text-nowrap absolute w-full h-screen flex justify-center items-center"
      >
        <div class="text-center font-bold px-4">
          <p class="text-xl mb-5 w-full max-w-md text-wrap">✋ Antes, por favor desative qualquer extensão de dark mode e depois clique em "OK"</p>
          <button class="px-4 py-2 bg-transparent border border-white cursor-pointer" @click="darkModeOff = true">OK</button>
        </div>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
  .fade-enter-active {
    transition: opacity 0.5s ease;
  }
  .fade-leave-active {
    transition: opacity 3s ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
</style>
