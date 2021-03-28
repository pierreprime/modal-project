<template>
  <h1>{{ title }}</h1>

  <!-- making use of Teleport -->
  <teleport to=".modals" v-if="showModal">
    <!-- listen to event emitted in modal -->
    <Modal
        :theme="currentTheme"
        :switchTheme="switchTheme"
        :toggleModal="toggleModal"
        @close="toggleModal"
    >
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <template v-slot:buttons>
        <button @click="switchTheme">Switch theme</button>
        <button @click="toggleModal">Close modal</button>
      </template>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showNewModal">
    <Modal
        :toggleModal="toggleModal2"
        @close="toggleModal2"
    >
      <h2>You are reading {{ title }}</h2>

    </Modal>
  </teleport>

  <button @click="toggleModal">Open modal</button>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br>
  <br><br>
  <br>
  <br>
  <button @click="toggleModal2">Open new modal</button>
</template>

<script>

// extra button, different modal
// same modal component, different template passed
// different method and data (toggleModal2

import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {Modal},
  data() {
    return {
      title: 'First Vue App !',
      header: 'Sign up for more',
      text: 'Blabla the best in the world',
      currentTheme: 'red',
      showModal: false,
      showNewModal: false
    }
  },
  methods: {
    switchTheme() {
      console.log('coucou')
      if (this.currentTheme === 'red')
        this.currentTheme = 'dark'
      else
        this.currentTheme = 'red'
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModal2() {
      this.showNewModal = !this.showNewModal
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
