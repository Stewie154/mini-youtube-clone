<template>
    <ul>
        <VideoListItem 
            v-for="video in videos" :key="video.title" 
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
            videos: Array
        }
    }
</script>

<style scoped>

</style>