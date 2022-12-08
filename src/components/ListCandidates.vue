<template>
    <Candidate :candidates="candidates"/>
</template>

<script>
import Candidate from "./Candidate.vue"

export default {
    name: "ListCandidates",
    props: {
        candidates: Array
    },
    components: {
        Candidate,
    }
}

</script>

