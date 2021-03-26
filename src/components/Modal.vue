<template>
  <!-- other method around than prop function : emit an event -->
  <!-- click.self : event triggered only for direct click in this element, not children -->
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ red: theme === 'red' }">
      <!-- fallback, nameless slot -->
      <slot>BABA</slot>
      <!-- named slot -->
      <slot name="buttons"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ['theme', 'switchTheme', 'toggleModal'],
  methods: {
    closeModal() {
      this.$emit('close')
    }
  }
}
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}

.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}

.modal p {
  font-style: normal;
}

.modal .buttons {
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .buttons button {
  color: darkgrey;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal.red {
  background: crimson;
  color: white;
}

.modal.red h1 {
  color: yellow;
}

.modal.red .buttons {
  color: white;
}

.modal.red .buttons button {
  color: white;
}

</style>