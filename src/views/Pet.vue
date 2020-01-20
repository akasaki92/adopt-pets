<template>
    <div>
        <h1>{{ animal.name }} ({{ $route.params.species}})</h1>
        <p>Age : {{ animal.age }} years old</p>
        <p>Breed : {{ animal.breed }}</p>
        <p>Color : {{animal.color}}</p>
        <p>Gender : {{animal.gender}}</p>
        <p>Location : {{animal.location}}</p>
        <p>Weight : {{animal.weight}}</p>
    </div>
</template>

<script>
import { mapState } from "vuex";

export default {
    data() {
        return {
            animal: {}
        };
    },
    computed: {
        ...mapState(["cats", "dogs"])
    },
    mounted() {
        const animal = this[this.$route.params.species][this.$route.params.id];
        this.animal = animal;
    }
};
</script>