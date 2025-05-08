<script setup lang="ts">
import { ref } from 'vue'

let light: boolean = ref(false)
let msg: string = ref('')

function toggleLight() {
  light.value = !light.value
}

function tentarSenha() {
  msg.value = '( ainda não terminei essa parte :[ )'

  setTimeout(() => {
    msg.value = ''
  }, 5000);
}
</script>

<template class="">
  <div :class="`bg-${light ? 'white' : 'black'}`" class="h-screen flex flex-col">
    <div>WIP Enigmas... (fala rapaziada!)</div>
    <div class="text-sm text-gray-500 mb-5 w-fit">
      <i>
        <strong>Aviso</strong>: não inspecione a página para resolver, pois isso é trapaça.
        <strong>explore</strong>
        a <strong class="underline">UI</strong> antes de tudo, ela vai te <strong class="cursor-pointer"
          @click="toggleLight" v-text="!light ? 'ocultar' : 'mostrar'"></strong> tudo que
        precisa para resolver.</i>
    </div>

    <div class="text-white w-full max-w-md mx-auto grow flex justify-center items-center border border-white">
      <form class="select-none" @submit.prevent="tentarSenha">
        <p class="text-black mb-5 text-2xl">Informe a senha:</p>
        <div class="flex gap-3 mb-5">
          <input type="number" class="bg-white text-black text-4xl px-2 w-14 cursor-default" required min="0" max="9">
          <input type="number" class="bg-white text-black text-4xl px-2 w-14 cursor-default" required min="0" max="9">
          <input type="number" class="bg-white text-black text-4xl px-2 w-14 cursor-default" required min="0" max="9">
          <input type="number" class="bg-white text-black text-4xl px-2 w-14 cursor-default" required min="0" max="9">
        </div>
        <div class="text-end mb-5">
          <button class="font-bold border border-white px-4 py-2 cursor-pointer" type="submit">Enviar</button>
        </div>
        <div>
          <p class="text-wrap text-center" v-text="msg"></p>
        </div>
      </form>
    </div>
  </div>
</template>
