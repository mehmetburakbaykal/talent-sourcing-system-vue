<template>
    <Candidate @delete-candidate="$emit('delete-candidate', candidate.id)" :candidates="candidates" />
</template>

<script>
import Candidate from "./Candidate.vue"

export default {
    name: "ListCandidates",
    props: {
        candidates: Array,
        candidate: Object
    },
    components: {
        Candidate,
    },
    emits: ['delete-candidate'],
}

</script>

