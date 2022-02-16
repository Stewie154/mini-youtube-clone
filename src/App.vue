<template>
    <div class="container">
        <SearchBar @searchSubmission="onSearchSubmission" />
        <div class="row">
            <VideoDetail :video="selected_video" />
            <VideoList @videoSelect="onVideoSelect" :videos="videos" :show_videos="show_videos"/>
        </div>
    </div>
</template>

<script>
    import SearchBar from './components/SearchBar.vue'
    import VideoList from './components/VideoList.vue'
    import VideoDetail from './components/VideoDetail.vue'
    import axios from 'axios'

    const API_KEY = 'AIzaSyBhkJqY8bT-40Kk7h2DDe4P60fzB3VWR-w'

    export default {
        name: 'App',
        components: {
            SearchBar,
            VideoList,
            VideoDetail
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
                show_videos: false,
                selected_video: null
            }
        },
        methods: {
             onVideoSelect(video) {
                this.selected_video = video
            },
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
            }
        }
    }
</script>