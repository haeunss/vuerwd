<template>

  <!-- 글목록페이지 -->
  <div v-if="step==0" class="insta-post">
    <InstaPost class="insta-post-image" :PostData="PostData[i]" v-for="(post,i) in PostData" :key="i"/>
  </div>

  <!-- 필터선택페이지 -->
  <div v-if="step==1">
    <div class="upload-image" :style="`background-image:url(${url})`"></div>
    <div class="filters">
      <div class="filter-1"></div>
      <div class="filter-1"></div>
      <div class="filter-1"></div>
      <div class="filter-1"></div>
      <div class="filter-1"></div>
    </div>
  </div>

  <!-- 글작성페이지 -->
  <div v-if="step==2">
    <div class="upload-image" :style="`background-image:url(${url})`"></div>
    <div class="write">
      <textarea class="write-box" placeholder="게시물을 작성해주세요." @input="$emit('write',$event.target.value)"></textarea>
    </div>
  </div>

</template>

<script>
import InstaPost from './InstaPost.vue'

export default {
  name: 'InstaContainer',
  components: {
    InstaPost: InstaPost,
  },
  props:{
    PostData:Array,
    step:Number,
    url:String,
  },
}
</script>

<style>
</style>