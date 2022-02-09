<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar.vue'
    import axios from 'axios'

    const API_KEY = 'AIzaSyDGTrGuucZY7IpGmjH333Ruy9hjQOgF0ek'

    export default {
        name: 'App',
        components: {
            SearchBar
        },
        methods: {
            onTermChange(searchTerm) {
                axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params: {
                        key: API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: searchTerm
                    }
                }).then(response => console.log(response))
            }
        }
    }
</script>