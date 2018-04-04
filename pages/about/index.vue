<template>
  <section id="about-page">
    <h1>{{ title }}</h1>
    <p>
      {{ content }}
    </p>
  </section>
</template>

<script>
export default {
  asyncData (context) {
    return context.app.$storyapi.get('cdn/stories/about', {
      version: context.isDev ? "draft" : "published",
    }).then((res) => {
      console.log('res', res)
      return {
        title: res.data.story.content.title,
        content: res.data.story.content.content
      }
    }).catch((res) => {
      context.error({ statusCode: res.response.status, message: res.response.data })
    })
  }
}
</script>

<style>
  #about-page {
    width: 80%;
    max-width: 500px;
  }

  #about-page p {
    white-space: pre-line;
  }
</style>
