<template>
    <div>
        <input @keyup.enter="onSearchSubmission"/>
    </div>
</template>

<script>
    export default {
        name: 'SearchBar',
        methods: {
            onSearchSubmission (event) {
                this.$emit('searchSubmission', event.target.value)
            }
        }
    }
</script>

<style scoped>
    input {
        width: 75%;
    }

    div {
        text-align: center;
        margin: 20px;
    }
</style>