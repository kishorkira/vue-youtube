<template>
    <div>
        <div class="embed-responsive embed-responsive-21by9">
            <iframe class="embed-responsive-item"
            width="560" height="315"
             :src="videoUrl" 
             frameborder="0" allow="autoplay; encrypted-media"
              allowfullscreen></iframe>

        </div>
    <div class="details">
         <h4>{{video.snippet.title}}</h4>
         <p>{{video.snippet.description}}</p>

    </div>
    </div>
</template>
<script>
export default {
    name:'VideoDetails',
    props:['video'],
    computed: {
        videoUrl:function(){
            const {videoId} = this.video.id;
            return  `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>
<style scoped>
    .details{
        margin-top: 10px;
        padding: 20px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }
</style>


