<template>
  <div v-if="showModal">
    <Modal
      :header="header"
      :text="text"
      theme="sale"
      @close="toggleShowModal"
    />
  </div>

  <h1>{{ title }}</h1>
  <br />
  <input type="text" ref="name" />
  <button @click="handleClick">click me</button>
  <button @click="toggleShowModal">Show modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My first Vue app :)",
      header: "Sign up for the giveaway!",
      text: "Grab your ninja swag for half the price",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.toggle("active");
      this.$refs.name.focus();
    },
    toggleShowModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid gray;
  display: inline-block;
}

.active {
  background-color: red;
}
</style>
