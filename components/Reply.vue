<template>
  <div class="comment-box replied" >
    <span class="commenter-pic">
      <img src="/v.png" class="img-fluid" />
    </span>
    <span class="commenter-name">
      <a href="#">{{ node.label }}</a>
      <span class="comment-time">2 hours ago</span>
    </span>
    <p class="comment-txt more">
        {{ node.content }}
    </p>
  </div>
</template>

<script>
export default {
    props: {
        node: Object
    }
}
</script>

<style lang="scss" scoped>
</style>