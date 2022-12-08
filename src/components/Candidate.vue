<template>
    <div class="list-container">
        <ul class="candidate-list">
            <li class="list-item" :key="candidate.id" v-for="candidate in candidates">
                <div class="wrapper">
                    <h3 class="full-name">
                        {{ candidate.fullName }}
                    </h3>
                    <div class="btn-container">
                        <button class="edit-btn"><i class="fa-solid fa-pen-to-square"></i></button>
                        <button class="delete-btn"><i class="fa-solid fa-xmark"></i></button>
                    </div>
                </div>
                <hr />
                <div class="contact-info">
                    <h4 class="phone-number">Phone Number: {{ candidate.phone }}</h4>
                    <h4 class="mail-address">E-mail: {{ candidate.mail }}</h4>
                    <h4 class="prev-interactions">{{ candidate.interactions }}</h4>
                    <h4 class="candidate-status">{{ candidate.status }}</h4>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Candidate",
    props: {
        candidate: Object,
        candidates: Array
    }
}
</script>

<style>
.list-container {
    width: 100vw;
    min-width: 520px;
}

.candidate-list {
    margin: 0.5%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: start;
    flex-wrap: wrap;
}

.list-item {
    width: 25%;
    min-width: 350px;
    background-color: rgb(211, 214, 219);
    margin-left: 0.5%;
    margin-bottom: 0.5%;
    padding: 0.5%;
    border: 2px solid black;
}

.wrapper {
    display: flex;
    justify-content: space-between;
}
</style>