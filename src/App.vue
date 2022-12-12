<template>
  <Header />
  <CreateCandidate :modalActive="modalActive" :toggleModal="toggleModal" :candidates="candidates" />
  <Modal @add-candidate="addCandidate" :toggleModal="toggleModal" :modalActive="modalActive" :candidates="candidates" />
  <ListCandidates @edit-candidate="editCandidate" @delete-candidate="deleteCandidate" :candidates="candidates"
    :toggleModal="toggleModal" :modalActive="modalActive" />
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
    ListCandidates, Modal,

  },
  data() {
    return {
      candidates: [],
      candidate: {
        fullName: '',
        phone: '',
        mail: '',
        interactions: '',
        status: ''
      }
    }
  },
  methods: {
    async addCandidate(candidate) {
      const res = await fetch('http://localhost:5000/candidates', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(candidate)
      });

      const data = await res.json();

      this.candidates = [...this.candidates, data]
    },

    editCandidate(id) {
      console.log(id);
    },

    async deleteCandidate(id) {
      if (confirm('Are you sure?')) {
        const res = await fetch(`http://localhost:5000/candidates/${id}`, {
          method: 'DELETE',
        })

        res.status === 200 ? (this.candidates = this.candidates.filter((candidate) => candidate.id !== id)
        ) : alert('Error deleting candidate')

      }
    },

    async fetchCandidates() {
      const res = await fetch('http://localhost:5000/candidates');

      const data = await res.json();

      return data;
    },
    async fetchCandidate(id) {
      const res = await fetch(`http://localhost:5000/candidates/${id}`);

      const data = await res.json();

      return data;
    },
  },

  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    }

    return { modalActive, toggleModal }
  },

  async created() {
    this.candidates = await this.fetchCandidates()
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
