<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
      <p>Search Term : {{searchTerm}}</p>
      <VideoDetails v-if="selectedVideo"
        :video="selectedVideo" 
      />
      <div>
        <VideoList :videos='videos' @videoSelect="onVideoSelect"></VideoList>
        
      </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetails from "./components/VideoDetails";
const API_KEY = "AIzaSyDC1zLsKm-jf_LjhbVYbiABjG9YKnH7WII";
export default {
  name: 'app',
  components : {
    SearchBar,
    VideoList,
    VideoDetails
  },
  data(){
    return{
      searchTerm : '',
      videos : [],
      selectedVideo:null
    }
  },
  methods : {
    onTermChange : function(searchTerm){
      this.searchTerm = searchTerm;
      axios
          .get("https://www.googleapis.com/youtube/v3/search",{
            params:{
              key: API_KEY,
              type:'viedo',
              part:'snippet',
              q: searchTerm
            }
          })
          .then(response => this.videos = response.data.items);
    },
    onVideoSelect(video){
      this.selectedVideo=video;
    }
  }
  
}
</script>

<style>

</style>
