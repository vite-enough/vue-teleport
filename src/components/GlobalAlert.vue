<script setup>
import { ref } from "vue";

const isOpen = ref(false);
</script>

<template>
  <button @click="isOpen = !isOpen">
    {{ isOpen ? "Close" : "Open" }} Modal
  </button>

  <Teleport to="body">
    <Transition mode="in-out">
      <div v-if="isOpen" class="modal">
        <p>I've been teleported here</p>
        <button class="close" type="button" @click="isOpen = false">
          Close
        </button>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
.modal {
  position: fixed;
  isolation: isolate;
  z-index: 1;
  top: 2rem;
  left: 2rem;
  width: 20rem;
  border: 1px solid grey;
  padding: 0.5rem;
  border-radius: 1rem;
  box-shadow: 2px 2px 4px grey;
  backdrop-filter: blur(4px);
  color: #f4f4f4;
}

button {
  padding: 0.5rem;
  border: 0;
  border-radius: 1rem;
  box-shadow: inset 0 -1px 4px grey, 1px 1px 4px grey;
  cursor: pointer;
  transition: box-shadow 0.15s ease-in-out;
}

button:hover {
  box-shadow: inset 0 -1px 2px grey, 1px 1px 2px grey;
}

.close {
  display: block;
  margin-left: auto;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.25s ease-in-out;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
  transform: translateX(-10vw);
}
</style>
