<template>
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleShowModal">
      <template v-slot:links>
        <a href="#">Sign up now!</a>
        <a href="#">More info</a>
      </template>

      <h1>Title</h1>
      <p>text under the title</p>
      <div class="close-btn" @click.self="toggleShowModal">X</div>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:something>
        <p>ja sam neki paragraf</p>
      </template>
      <p>Nesto tek toliko</p>
    </Modal>
  </teleport>

  <h1>{{ title }}</h1>
  <br />
  <input type="text" ref="name" />
  <br />
  <button @click="handleClick">click me</button>
  <br />
  <button @click="toggleShowModal">Show modal</button>
  <br />
  <button @click="toggleModalTwo">Another one</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My first Vue app :)",
      showModal: false,
      showModalTwo: false,
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
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
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

.close-btn {
  display: inline-block;
  background-color: black;
  border-radius: 50%;
  padding: 5px 9px;
  cursor: pointer;
}
</style>
