<template>
    <li @click="onVideoSelect" class="list-group-item media d-flex">
        <img v-if="thumbnailUrl" :src="thumbnailUrl" class="mr-3" alt="thumbnail">
        <div class="media-body">
            {{video.snippet.title}}
        </div>
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: {
            video: Object
        },
        methods: {
            onVideoSelect() {
                this.$emit('videoSelect', this.video)
            }
        },
        computed: {
            thumbnailUrl() {
                return this.video.snippet.thumbnails.default.url
            }
        }
    }
</script>

<style scoped>
    li {
        cursor: pointer;
    }

    li:hover {
        background: #eee;
    }

    .mr-3 {
        margin-right: 1rem;
    }
</style>