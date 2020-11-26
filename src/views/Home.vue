<template>
  <div class="home section bg-white">
    <div class="container flow-content">
      <h1 class="h2">Welcome to Your Vue.js App</h1>

      <v-message type="is-primary" shadow v-model="alert" v-if="alert" hasFooter>
        <template v-slot:message-header>Hello</template>
        <template v-slot:message-body>
          hello world! <a href="">click me</a> <strong>Soy de confianza</strong> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque risus mi, tempus quis placerat ut, porta nec nulla.Nullam gravida purus diam, et dictum felis venenatis efficitur. Aenean ac eleifend lacus, in mollis lectus.Aenean ac eleifend lacus, in mollis lectus.Aenean ac eleifend lacus, in mollis lectus.
        </template>
        <template v-slot:message-footer>
          <div class="buttons">
            <v-button class="is-primary" icon="fas fa-skull-crossbones">Confirm</v-button>
            <v-button class="is-danger is-light">Cancel</v-button>
          </div>
        </template>
      </v-message>

    </div>
  </div>
</template>
<script>
import Message from '@/components/lib/Message.vue';
import Button from '@/components/lib/Button.vue';
export default {
  components: {
    'v-message': Message,
    'v-button': Button
  },
  data() {
    return {
      alert: true
    }
  }
}
</script>