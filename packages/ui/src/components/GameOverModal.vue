<template>
  <div
    class="bg-beige px-4 pt-5 pb-4 sm:p-6 sm:pb-4"
    :class="RANCHES[player?.ranch?.name]"
  >
    <div class="sm:flex sm:items-start">
      <div
        class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-beige sm:mx-0 sm:h-10 sm:w-10"
      >
        <SvgImage :svg="bufficornMain" />
      </div>
      <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
        <h3
          class="text-lg leading-6 font-medium text-gray-900"
          id="modal-title"
        >
          Please connect to a Web3 provider
        </h3>
        <div class="mt-2">
          <p class="text-sm text-gray-900">
            You need to connect to Polygon Mainnet via your favorite Web3
            provider (e.g. MetaMask) to mint your NFTs. Please, create a backup
            of your profile from the main menu in case you need to move to
            another device.
          </p>
        </div>
      </div>
    </div>
  </div>
  <div class="bg-beige px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
    <button
      :class="RANCHES[player?.ranch?.name]"
      @click="$parent.$emit('close')"
      type="button"
      class="mt-3 w-full inline-flex justify-center rounded-md border-primary shadow-sm px-4 py-2 bg-transparent text-base font-bold text-brown hover:bg-transparent focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
    >
      CLOSE
    </button>
  </div>
</template>

<script>
import { defineComponent, getCurrentInstance } from 'vue'
import { useWeb3 } from '../composables/useWeb3'
import { useStore } from '@/stores/player'
import bufficornMain from '@/assets/wittyCorn.svg?raw'
import { RANCHES } from '@/constants.js'

export default defineComponent({
  setup (props, ctx) {
    const instance = getCurrentInstance()
    const w3Witmon = useWeb3()
    const player = useStore()

    return {
      player,
      bufficornMain,
      RANCHES,
      mint () {
        instance.parent.emit('close')
      }
    }
  }
})
</script>
