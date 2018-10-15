<template>
    <ul class="list-group list-unstyled">
        <VideoListItem 
            v-for="video in videos" 
            :key="video.etag"
            :video="video"
            @videoSelect="onVideoSelect" />
       
    </ul>
    
</template>
<script>
import VideoListItem from "./VideoListItem"
export default {
    name: 'VideoList',
    components:{
        VideoListItem
    },
    props:['videos'],
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect',video);
        }
    }
}
</script>
<style scoped>

</style>

