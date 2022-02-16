<template>
    <ul class="list-group col-md-4" v-if="show_videos == true">
        <VideoListItem 
            v-for="video in videos" 
            :key="video.etag" 
            :video="video"
            @videoSelect="onVideoSelect"
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
        },
        methods: {
            onVideoSelect(video) {
                this.$emit('videoSelect', video)
            }
        }
    }
</script>

<style scoped>

</style>