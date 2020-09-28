<template>
  <div class="container">
    <v-card class="mx-auto" outlined>
      <v-list-item three-line>
        <v-list-item-content>
          <div class="overline mb-4">Topic</div>
          <v-list-item-title class="headline mb-1"
            >Post Title</v-list-item-title
          >
          <v-list-item-subtitle>Post Description</v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-avatar tile size="80" color="grey"></v-list-item-avatar>
      </v-list-item>

      <v-card-actions>
        <v-btn text>No of Comments</v-btn>
        <v-btn text>Created By</v-btn>
      </v-card-actions>
    </v-card>

    <div class="row">
      <div class="col-12">
        <div class="comments">
          <div class="comments-details">
            <span class="total-comments comments-sort">117 Comments</span>
            <span class="dropdown">
              <button
                type="button"
                class="btn dropdown-toggle"
                data-toggle="dropdown"
              >
                Sort By <span class="caret"></span>
              </button>
              <div class="dropdown-menu">
                <a href="#" class="dropdown-item">Top Comments</a>
                <a href="#" class="dropdown-item">Newest First</a>
              </div>
            </span>
          </div>
          <div class="comment-box add-comment">
            <span class="commenter-pic">
              <img src="/images/user-icon.jpg" class="img-fluid" />
            </span>
            <span class="commenter-name">
              <input
                type="text"
                placeholder="Add a public comment"
                name="Add Comment"
              />
              <button type="submit" class="btn btn-default">Comment</button>
              <button type="cancel" class="btn btn-default">Cancel</button>
            </span>
          </div>
          <div class="comment-box">
            <span class="commenter-pic">
              <img src="/images/user-icon.jpg" class="img-fluid" />
            </span>
            <span class="commenter-name">
              <a href="#">Happy uiuxStream</a>
              <span class="comment-time">2 hours ago</span>
            </span>
            <p class="comment-txt more">
              Suspendisse massa enim, condimentum sit amet maximus quis,
              pulvinar sit amet ante. Fusce eleifend dui mi, blandit vehicula
              orci iaculis ac.
            </p>
            <div class="comment-meta">
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
            <div class="comment-box add-comment reply-box" v-show="!isNinja">
              <span class="commenter-pic">
                <img src="/images/user-icon.jpg" class="img-fluid" />
              </span>
              <span class="commenter-name">
                <input
                  type="text"
                  placeholder="Add a public reply"
                  name="Add Comment"
                />
                <button type="submit" class="btn btn-default">Reply</button>
                <button type="cancel" class="btn btn-default reply-popup">
                  Cancel
                </button>
              </span>
            </div>
          </div>
          <div class="comment-box">
            <span class="commenter-pic">
              <img src="/images/user-icon.jpg" class="img-fluid" />
            </span>
            <span class="commenter-name">
              <a href="#">Happy uiuxStream</a>
              <span class="comment-time">2 hours ago</span>
            </span>
            <p class="comment-txt more">
              Suspendisse massa enim, condimentum sit amet maximus quis,
              pulvinar sit amet ante. Fusce eleifend dui mi, blandit vehicula
              orci iaculis ac.
            </p>
            <div class="comment-meta">
              <button class="comment-like">
                <i class="fa fa-thumbs-o-up" aria-hidden="true"></i> 99
              </button>
              <button class="comment-dislike">
                <i class="fa fa-thumbs-o-down" aria-hidden="true"></i> 149
              </button>
              <button class="comment-reply">
                <i class="fa fa-reply-all" aria-hidden="true"></i> Reply
              </button>
            </div>
            <div class="comment-box replied">
              <span class="commenter-pic">
                <img src="/images/user-icon.jpg" class="img-fluid" />
              </span>
              <span class="commenter-name">
                <a href="#">Happy uiuxStream</a>
                <span class="comment-time">2 hours ago</span>
              </span>
              <p class="comment-txt more">
                Suspendisse massa enim, condimentum sit amet maximus quis,
                pulvinar sit amet ante. Fusce eleifend dui mi, blandit vehicula
                orci iaculis ac.
              </p>
              <div class="comment-meta">
                <button class="comment-like">
                  <i class="fa fa-thumbs-o-up" aria-hidden="true"></i> 99
                </button>
                <button class="comment-dislike">
                  <i class="fa fa-thumbs-o-down" aria-hidden="true"></i> 149
                </button>
                <button class="comment-reply">
                  <i class="fa fa-reply-all" aria-hidden="true"></i> Reply
                </button>
              </div>
              <div class="comment-box replied">
                <span class="commenter-pic">
                  <img src="/images/user-icon.jpg" class="img-fluid" />
                </span>
                <span class="commenter-name">
                  <a href="#">Happy uiuxStream</a>
                  <span class="comment-time">2 hours ago</span>
                </span>
                <p class="comment-txt more">
                  Suspendisse massa enim, condimentum sit amet maximus quis,
                  pulvinar sit amet ante. Fusce eleifend dui mi, blandit
                  vehicula orci iaculis ac.
                </p>
                <div class="comment-meta">
                  <button class="comment-like">
                    <i class="fa fa-thumbs-o-up" aria-hidden="true"></i> 99
                  </button>
                  <button class="comment-dislike">
                    <i class="fa fa-thumbs-o-down" aria-hidden="true"></i> 149
                  </button>
                  <button class="comment-reply">
                    <i class="fa fa-reply-all" aria-hidden="true"></i> Reply
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isNinja: true,
    }
  },
}
</script>

<style>

</style>