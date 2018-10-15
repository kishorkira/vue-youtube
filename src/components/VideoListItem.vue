<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-3" :src="thumbnailUrl" alt="video.snippet.title">
        <div class="media-body">
            {{title}}
        </div>
    </li>
</template>
<script>
export default {
    name: 'VideoListItem',
    data(){
        return {};
    },
    props:['video'],
    methods:{
        onVideoSelect(){
            this.$emit('videoSelect',this.video);
        }
    },
    computed: {
        thumbnailUrl:function(){
            return this.video.snippet.thumbnails.default.url;
        },
        title:function(){
            return this.video.snippet.title;
        }
    }
}
</script>
<style scoped>
    li{
        display: flex;
        cursor: pointer;
    }
    li:hover{
        background-color: #eee;
    }
</style>
