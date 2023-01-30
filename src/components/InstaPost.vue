<template>
  <div class="post">
    <div class="post-header">
      <div class="profile" :style="{backgroundImage:`url(${PostData.userImage})`}"></div>
      <span class="profile-name">{{ PostData.name }}</span>
    </div>
    <div class="post-body" :style="{backgroundImage:`url(${PostData.postImage})`}"></div>
    <div class="post-content">
      <p>{{ PostData.likes }}명이 좋아합니다</p>
      <p><strong>{{ PostData.name }}</strong>{{ PostData.content }}</p>
      <p class="date">{{ PostData.date }}</p>
    </div>
  </div> 
</template>

<script>

export default {
  name: 'InstaPost',
  components: {
  },
  props:{
    PostData:Object,
  }
}
</script>

<style>
</style>