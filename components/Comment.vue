<template>
  <!-- <li class="node-tree">
    <span class="label">{{ node.label }}</span>

    <ul v-if="node.children && node.children.length">
      <node :key="child.label" v-for="child in node.children" :node="child"></node>
    </ul>
  </li> -->
  <div class="comments">
    <div class="comment-box">
      <span class="commenter-pic">
        <img src="/v.png" class="img-fluid" />
      </span>
      <span class="commenter-name">
        <a href="#">{{ post.label }}</a>
        <span class="comment-time">2 hours ago</span>
      </span>
      <p class="comment-txt more">
        {{ post.content }}
      </p>
      <div v-if="post.children && post.children.length">
          <Reply :key="child.label" v-for="child in post.children" :node="child"/>
      </div>
    </div>
  </div>
</template>

<script>
import Reply from './Reply'

export default {
  components: {
    Reply,
  },

  data: () => ({
    post: {
      id: 1,
      label: 'Main Comment',
      parent: null,
      is_reply: false,
      card: 1,
      created_by: 3,
      children: [
        {
          id: 2,
          label: 'Reply Comment',
          parent: 1,
          is_reply: true,
          card: 1,
          created_by: 3,
          children: [
            {
              id: 4,
              label: 'Another Reply To Comment 2',
              parent: 2,
              is_reply: true,
              card: 1,
              created_by: 3,
              children: [],
            },
            {
              id: 5,
              label: 'Another Reply To Comment 2',
              parent: 2,
              is_reply: true,
              card: 1,
              created_by: 3,
              children: [],
            },
          ],
        },
        {
          id: 3,
          label: 'Reply Comment 2',
          parent: 1,
          is_reply: true,
          card: 1,
          created_by: 3,
          children: [],
        },
      ],
    },
  }),
}
</script>

<style lang="scss" scoped>
</style>