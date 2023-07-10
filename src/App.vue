<template>
  <h1>{{ title }}</h1>
  <p>Welcome ...</p>
  <teleport to=".modals" v-if="showModal">
    <Modal @close="toggleModal" theme="sale">
      <template v-slot:links>
        <a href="">sign up now</a>
        <a href="">more info</a>
        <a href="">contact info</a>
      </template>
      <h1>{{ header }}</h1>
      <p>heelo</p>
    </Modal>
  </teleport>
  <teleport to="#app" v-if="showSecondModal">
    <Modal @close="toggleSecondModal" theme="hello"> hello </Modal>
  </teleport>
  <button @click="toggleModal">open modal</button>
  <button @click="toggleSecondModal">open second modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign up for the cause!",
      description: "We're trying to make the world a better place.",
      showModal: false,
      showSecondModal: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleSecondModal() {
      this.showSecondModal = !this.showSecondModal;
    },
  },
};
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
