<template>
  <v-col cols="12">
    <v-card max-width="800" class="mx-auto">
      <v-list-item>
        <v-list-item-avatar v-if="post.avatar" color="grey">
          <g-image
            :src="post.avatar"
            width="180"
            height="180"
            blur="5"
            alt="avatar"
          />
        </v-list-item-avatar>
        <v-list-item-content>
          <h2 class="headline"><g-link :to="$url(post.path)">{{ post.title }}</g-link>
            
          </h2>
          <post-meta :post="post" />
          <v-list-item-subtitle v-if="post.author"
            >by {{ post.author }}</v-list-item-subtitle
          >
        </v-list-item-content>
      </v-list-item>

      <v-img
        v-if="post.cover_image"
        alt="Cover image"
        :aspect-ratio="16 / 9"
        :src="post.cover_image"
      />

      <v-card-text>{{ post.description }}</v-card-text>
      <v-divider />
      <v-card-actions>
        <post-tags :post="post" />
        <v-spacer />
        <v-btn color="primary" router dark :to="$url(post.path)">Read</v-btn>
      </v-card-actions>
    </v-card>
  </v-col>
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'

export default {
  components: {
    PostMeta,
    PostTags
  },
  props: ['post']
}
</script>
