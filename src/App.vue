<template>
  <div class="header">
    <ul class="header-button-left">
      <li v-if="step>0" @click="step=0">Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li v-if="step==1" @click="step++">Next</li>
      <li v-if="step==2" @click="publish">Write</li>
    </ul>
    <img src="./assets/images/instagram.png" class="logo" />
  </div>

  <InstaContainer :PostData="PostData" :step="step" :url="url" @write="NewPost = $event" />
  <button @click="more" v-if="step==0">더보기</button>

  <div class="footer">
    <ul class="footer-button-plus">
      <input @change="upload" multiple accept="image/*" type="file" id="file" class="inputfile" />
      <label for="file" class="input-plus">+</label>
    </ul>
  </div>

</template>

<script>
import InstaContainer from './components/InstaContainer.vue'
import PostData from './assets/PostData.js'
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return{
      step: 0,
      PostData: PostData,
      MorePost: 0,
      url: '',
      NewPost:'',
    }
  },
  components: {
    InstaContainer: InstaContainer,
  },
methods:{
  more(){
    // axios.post('URL',{name:'kim'}).then().catch((err)=>{err})
    axios.get(`https://codingapple1.github.io/vue/more${this.MorePost}.json`)
    .then(result=>{
      console.log(result.data);
      this.PostData.push(result.data);   
      this.MorePost++;
    })
  },
  upload(e){
    let file = e.target.files;
    let url = URL.createObjectURL(file[0]);
    console.log(url);
    this.url = url;
    this.step++;
  },
  publish(){
    var myPost = {
      name: "eunie___day ",
      userImage: "https://placeimg.com/100/100/arch",
      postImage: this.url,
      likes: 36,
      date: "May 15",
      liked: false,
      content: this.NewPost,
      filter: "perpetua"
    };
    this.PostData.unshift(myPost);
    this.step=0;
  }
},

}
</script>

<style>
</style>
