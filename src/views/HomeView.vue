<template>
  <div class="home">
    <transition name="toast">
      <Toast v-if="showToast" />
    </transition>
    <Todos @badValue="triggerToast" />
  </div>
</template>

<script>
import { ref } from "vue";
import Toast from "../components/Toast.vue";
import Todos from "../components/Todos.vue";

export default {
  components: { Toast, Todos },

  setup() {
    const showToast = ref(false);

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => (showToast.value = false), 3000);
    };
    return { showToast, triggerToast };
  },
};
</script>

<style scoped>
/* enter classes */
/* This first class could be 'apagada' cause the starter point is a default values, like opacity is always gonna be 1, for example */
.toast-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}
.toast-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.toast-enter-active {
  transition: all 0.3s ease;
}

/* leave classes */
.toast-leave-from {
  opacity: 1;
  transform: translateY(0);
}

.toast-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}

.toast-leave-active {
  transition: all 0.3s ease;
}
</style>