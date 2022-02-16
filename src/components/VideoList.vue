<template>
    <ul class="list-group" v-if="show_videos == true">
        <VideoListItem 
            v-for="video in videos" 
            :key="video.etag" 
            :video="video"
        />
    </ul>
</template>

<script>
    import VideoListItem from './VideoListItem.vue'
    export default {
        name: 'VideoList',
        components: {
            VideoListItem
        },
        props: {
            videos: Array,
            show_videos: Boolean
        }
    }
</script>

<style scoped>

</style>