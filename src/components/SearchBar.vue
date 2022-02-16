<template>
    <div>
        <input @input="onInput" @keyup.enter="onSearchSubmission"/>
    </div>
</template>

<script>
    export default {
        name: 'SearchBar',
        methods: {
            onInput (event) {
                this.$emit('termChange', event.target.value)
            },
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