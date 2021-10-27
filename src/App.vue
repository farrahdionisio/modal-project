<template>
  <div>
    <h1>{{ title }}</h1>
    <p>Welcome...</p>
    <teleport to=".modals" v-if="showModal">
      <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">Sign up now</a>
          <a href="#">More info</a>
        </template>
      </Modal>
    </teleport>
    <div v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <h1>Sign up to newsletter</h1>
        <p>For updates and promo codes</p>
      </Modal>
    </div>
    <button @click="toggleModal">Open Modal</button> <br />
    <button @click="toggleModalTwo">Open Modal Two</button>
  </div>
</template>

<script>
import Modal from "./components/Modal";

export default {
  name: "App",
  data() {
    return {
      title: "My First Vue App",
      header: "Sign up for the giveaway!",
      text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },

    toggleModal() {
      this.showModal = !this.showModal;
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
  components: {
    Modal,
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
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
