<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="videos"/>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar.vue'
    import VideoList from './components/VideoList.vue'
    import axios from 'axios'

    const API_KEY = 'AIzaSyDGTrGuucZY7IpGmjH333Ruy9hjQOgF0ek'

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList
        },
        data() {
            return {
                videos: []
            }
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
                }).then(response => 
                    this.videos = response.data.items
                )
            }
        }
    }
</script>