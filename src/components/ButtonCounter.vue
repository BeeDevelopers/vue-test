<script setup>
import { ref } from 'vue'

const props = defineProps(['descr'])
const emit = defineEmits(['counter'])

const btnClass = ref(true)

const addCounter = () => {
  btnClass.value = !btnClass.value
  emit('counter', 1)
}

console.log(props.descr)
</script>

<template>
  <button :class="{ btnCounter: btnClass }" @click="addCounter">
    {{ props.descr }}
  </button>
</template>

<style scoped>
.btnCounter {
  color: red;
}
</style>
