<template>
  <section class="container">
    <PostPreview
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      :excerpt="post.previewText"
      :thumbnailImage="post.thumbnailUrl"
      :id="post.id" />
  </section>
</template>

<script>
import PostPreview from "@/components/Blog/PostPreview";

export default {
  data () {
    return {
      posts: [
        {
          title: 'A new beginning',
          previewText: 'This will be awesome, don\'t miss it...',
          thumbnailUrl: 'http://www.readersdigest.ca/wp-content/uploads/2013/02/worst-foods-for-aging-fast-food.jpg',
          id: 'a-new-beginning'
        },
        {
          title: 'A Second beginning',
          previewText: 'This will be awesome, don\'t miss it...',
          thumbnailUrl: 'http://www.readersdigest.ca/wp-content/uploads/2013/02/worst-foods-for-aging-fast-food.jpg',
          id: 'a-second-beginning'
        }
      ]
    }
  },
  components: {
    PostPreview
  }
}
</script>

<style>
  #posts {
    padding-top: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  @media (min-width: 35rem) {
    #posts {
      flex-direction: row;
    }
  }
</style>