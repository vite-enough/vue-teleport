# Vue 3 + Vite

How to use the `Teleport` component

More info at https://vuejs.org/guide/built-ins/teleport.html

```js
<script setup>
  import { ref } from "vue";
  const isOpen = ref(false);
</script>

<template>
  <Teleport to="body">
    <div v-if="isOpen" class="modal">
      <p>I've been teleported here</p>
      <button class="close" type="button" @click="isOpen = false">
        Close
      </button>
    </div>
  </Teleport>
</template>
```
