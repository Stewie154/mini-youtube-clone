<template>
    <li @click="onClick(video)">{{video.snippet.title}}</li>
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