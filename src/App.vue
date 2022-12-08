<template>
  <Header />
  <CreateCandidate :toggleModal="toggleModal" />
  <ListCandidates :candidates="candidates" />
  <Modal :toggleModal="toggleModal" :modalActive="modalActive" />
</template>

<script>
import Header from "./components/Header.vue"
import CreateCandidate from "./components/CreateCandidate.vue"
import ListCandidates from "./components/ListCandidates.vue"
import Modal from "./components/Modal.vue"
import { ref } from "vue"


export default {
  name: 'App',
  components: {
    Header,
    CreateCandidate,
    ListCandidates,
    Modal
  },
  data() {
    return {
      candidates: [],
    }
  },
  created() {
    this.candidates = [
      {
      id: 1,
      fullName: 'Mehmet Burak Baykal',
      phone: '05066920750',
      mail: 'burak@gmail.com',
      interactions: 'Interviewing',
      status: 'Called'
    },
  {
    id: 1,
      fullName: 'Test Test',
      phone: '053256598',
      mail: 'test@gmail.com',
      interactions: 'Hiring',
      status: 'Mail sent'
  }]
  },

  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    }

    return { modalActive, toggleModal }
  },

}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Heebo&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Heebo", sans-serif;
  text-decoration: none;
  list-style-type: none;
}
</style>
