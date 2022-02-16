<template>
    <li
        @click="onClick(video)"
        class="list-group-item"
    >
        <img :src="thumbnailUrl" alt="">
        {{video.snippet.title}}
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: {
            video: Object
        },
        methods: {
            onClick: (video) => {
                console.log(video)
            }
        },
        computed: {
            thumbnailUrl() {
                return this.video.snippet.thumbnails.default.url
            }
        }
    }
</script>