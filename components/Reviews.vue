<template>
    <div>
        <h3>Customer Reviews</h3>
        <div v-if="!$fetchState.pending">
            <ReviewCard
                v-for="rev in reviewers.results"
                :key="rev.login.uuid"
                :review="rev"
            />
        </div>
        <div v-else>
            Loading...
        </div>
    </div>
</template>

<script>
import ReviewCard from './ReviewCard.vue'
    export default {
        data() {
            return {
                reviewers: [],
            }
        },
        async fetch() {
            this.reviewers = await fetch(
                "https://randomuser.me/api/?results=5"
            ).then(res => res.json())
        }
    }
</script>

<style lang="scss" scoped>

</style>