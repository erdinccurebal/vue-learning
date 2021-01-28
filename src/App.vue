<template>
  <div>
    <slot-test>
      <h1>Title</h1>
      <template #posts>
        <div v-for="post in posts" :key="post.id">
          <h2>{{ post.title }}</h2>
          <p>{{ post.content }}</p>
        </div>
      </template>
    </slot-test>
  </div>
</template>

<script>
import SlotTest from "./components/SlotTest";

export default {
  components: {
    SlotTest,
  },
  data() {
    return {
      posts: [],
    };
  },
  created() {
    setTimeout(() => {
      this.posts = [
        {
          id: 1,
          title: "Lorem Title 12312323",
          content: "Lorem Content 123435341",
        },
        { id: 2, title: "Lorem Title 45632", content: "Lorem Content 763121" },
        {
          id: 3,
          title: "Lorem Title 34212131",
          content: "Lorem Content 3424234",
        },
      ];
    }, 2000);
  },
};
</script>