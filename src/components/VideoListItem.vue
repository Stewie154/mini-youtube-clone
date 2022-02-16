<template>
    <li
        @click="onClick(video)"
        class="list-group-item"
    >
        <img :src="video.snippet.thumbnails.default.url" alt="">
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
        }
    }
</script>