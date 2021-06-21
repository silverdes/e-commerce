<template>
    <div class="relative flex items-center">
            <button class="focus:outline-none" @click="toggle">
            <slot name="icon"></slot>
            </button>
        <div class="bg-green-400 h-4 w-4 flex justify-center items-center rounded-full absolute -top-1 -right-2">
            <slot name="highlight"></slot>
         </div>
        <div class="flex w-52 absolute bg-white shadow-md rounded-md absolute top-7 z-10 mt-3 right-0.5 border border-gray-100" v-if="isVisible" v-click-away="onClickAway">
            <slot name="dropdown">
            </slot>
        </div>
    </div>           
</template>

<script>
export default {
 data() {
    return {
      isVisible: false,
    };
  },
  methods: {
    toggle() {
      this.isVisible = !this.isVisible;
    },
    onClickAway() {
      this.isVisible = false;
    },
  },
}
</script>

<style>

</style>