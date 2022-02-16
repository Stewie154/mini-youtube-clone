<template>
    <div class="container">
        <SearchBar @searchSubmission="onSearchSubmission" />
        <VideoList :videos="videos" :show_videos="show_videos"/>
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
            onTermChange(searchTerm) {
                axios.get('https://www.googleapis.com/youtube/v3/search', {
                    params: {
                        key: API_KEY,
                        type: 'video',
                        part: 'snippet',
                        q: searchTerm
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
            onSearchSubmission(searchSubmission) {
                console.log(searchSubmission);
            }
        }
    }
</script>