<template>
    <div class="home"></div>
    <Modal :modalActive="modalActive" />
</template>

<script>
import Modal from "../components/Modal.vue"
import { ref } from "vue"
export default {
    name: "Home",
    components: {
        Modal
    },
    setup() {
        const modalActive = ref(true);

        return { modalActive }
    }
}
</script>