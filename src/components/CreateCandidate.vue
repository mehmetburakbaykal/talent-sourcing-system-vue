<template>
    <button @click="toggleModal" class="create-btn"><i class="fa-solid fa-plus fa-xl"></i></button>
    <Modal :toggleModal="toggleModal" :modalActive="modalActive" :candidates="candidates" />

</template>

<script>
import Modal from "./Modal.vue"

export default {
    name: "CreateCandidate",
    components: {
        Modal,
    },
    props: {
        modalActive: Boolean,
        toggleModal: Function,
        candidates: Array
    }
}

</script>

<style>
.create-btn {
    background-color: #00b900;
    position: relative;
    float: right;
    margin-top: 2px;
    margin-right: 2px;
    border: 1px solid #00b900;
    border-radius: 5px;
    cursor: pointer;
}

.create-btn>i {
    margin: 25px 40px;
    color: #ffff;
}
</style>