<template>
    <div class="container">
        <SearchBar @searchSubmission="onSearchSubmission" />
        <VideoList @videoSelect="onVideoSelect" :videos="videos" :show_videos="show_videos"/>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar.vue'
    import VideoList from './components/VideoList.vue'
    import axios from 'axios'

    const API_KEY = 'AIzaSyBhkJqY8bT-40Kk7h2DDe4P60fzB3VWR-w'

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList
        },
        data() {
            return {
                videos: [
                    {
                        snippet: {
                            title: 'Request Failed, default title'
                        }
                    },
                    {
                        snippet: {
                            title: 'Request Failed, default title'
                        }
                    },
                    {
                        snippet: {
                            title: 'Request Failed, default title'
                        }
                    },
                    {
                        snippet: {
                            title: 'Request Failed, default title'
                        }
                    },
                    {
                        snippet: {
                            title: 'Request Failed, default title'
                        }
                    }
                ],
                show_videos: false
            }
        },
        methods: {
            onSearchSubmission(searchSubmission) {
                axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params: {
                        key: API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: searchSubmission
                    }
                }).then(response => {
                    this.show_videos = true
                    if (response != undefined) {
                        this.videos = response.data.items
                    }
                }).catch(error => {
                    this.show_videos = true
                    this.videos.forEach(video => {
                        video.snippet.title = error
                    });
                })
            },
            onVideoSelect(video) {
                console.log(video)
            }
        }
    }
</script>