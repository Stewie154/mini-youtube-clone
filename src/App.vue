<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar.vue'
    const API_KEY = 'AIzaSyDGTrGuucZY7IpGmjH333Ruy9hjQOgF0ek'
    
    export default {
        name: 'App',
        components: {
            SearchBar
        },
        methods: {
            onTermChange(searchTerm) {
                console.log(searchTerm)
            }
        }
    }
</script>