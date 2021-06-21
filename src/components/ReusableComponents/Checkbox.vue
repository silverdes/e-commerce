<template>
    <label for="accessories" class="py-1 px-2 rounded-md bg-gray-100 border border-gray-200">
      <slot></slot>
    </label>
  <input type="checkbox" id="accessories" class="hidden" v-model="colors" value="red"/>
</template>

<script>
export default {

}
</script>

<style scoped>

</style>