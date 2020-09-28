<template>
  <div class="comments">
    <div class="comment-box">
      <span class="commenter-pic">
        <img src="/v.png" class="img-fluid" />
      </span>
      <span class="commenter-name">
        <a href="#">{{ reply.label }}</a>
        <span class="comment-time">2 hours ago</span>
      </span>
      <p class="comment-txt more">
        {{ reply.content }}
      </p>
      <div class="comment-meta">
        <p>
          <strong>@</strong><em>{{ reply.created_by }}</em>
        </p>
        <button class="comment-like">
          <i class="fa fa-thumbs-o-up" aria-hidden="true"></i> 99
        </button>
        <button class="comment-dislike">
          <i class="fa fa-thumbs-o-down" aria-hidden="true"></i> 149
        </button>
        <button
          class="comment-reply reply-popup"
          v-on:click="isNinja = !isNinja"
        >
          <i class="fa fa-reply-all" aria-hidden="true"></i> Reply
        </button>
      </div>
      <div v-if="reply.children && reply.children.length">
        <reply
          :key="child.label"
          v-for="child in reply.children"
          :reply="child"
        ></reply>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'reply',
  props: {
    reply: Object,
  },
}
</script>

<style lang="scss" scoped></style>
