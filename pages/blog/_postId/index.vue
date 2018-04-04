<template>
  <div id="post" v-editable="block">
    <div class="post-thumbnail" :style="{backgroundImage: 'url('+ image +')'}"></div>
    <div class="post-content">
      <h1>{{ title }}</h1>
      <p>{{ content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  asyncData (context) {
    return context.app.$storyapi.get(`cdn/stories/blog/${context.params.postId}`, {
      version: context.isDev ? "draft" : "published",
    }).then((res) => {
      console.log('res', res.data)
      return {
        block: res.data.story.content,
        image: res.data.story.content.thumbnail,
        title: res.data.story.content.title,
        content: res.data.story.content.content
      }
    }).catch((res) => {
      // context.error({ statusCode: res.response.status, message: res.response.data })
    })
  },
  mounted () {
    this.$storyblok.init()
    this.$storyblok.on('change', ()=>{
      location.reload(true)
    })
  }
}
</script>

<style>
.post-thumbnail {
  width: 100%;
  height: 300px;
  background-size: cover;
  background-position: center;
}

.post-content {
  width: 80%;
  max-width: 500px;
  margin: auto;
}
</style>
