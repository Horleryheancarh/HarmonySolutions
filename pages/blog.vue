<template>
  <v-app dark>
    <v-btn to="/" color="success">Home Page</v-btn>
    <h1>Under Construction</h1>
    <v-banner v-for="(post, i) in posts" :key="i" two-line>
      <v-avatar slot="icon" color="deep-purple accent-4" size="40">
        <v-icon color="white"> {{ post.icon }} </v-icon>
      </v-avatar>
      <h3>{{ item.title }}</h3>
      {{ item.content }}
      <template #:actions>
        <v-btn text :to="item.to" color="deep-purple accent-4"> Read </v-btn>
      </template>
    </v-banner>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {
          icon: 'mdi-apps',
          title: 'Post1',
          content: 'This is the details of the post',
          to: '/',
        },
      ],
    };
  },
};
</script>
