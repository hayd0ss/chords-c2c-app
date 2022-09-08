<template>
  <div class="comment-container">
    <div class="post-comment">
      <h4>Post a Comment</h4>
      <textarea
        placeholder="Your comment here..."
        name="type-comment"
        id=""
        cols="60"
        rows="13"
      ></textarea>

      <div class="button-container">
        <button class="purchase">SUBMIT COMMENT</button>
      </div>
    </div>

    <div class="view-comment-container">
      <div class="mock-comment">
        <img
          src="../assets/images/SebastianStanvalentino.jpeg"
          alt=""
        />
        <div class="comment-container">
          <h4>honicz</h4>
          <p>I really like the artwork of this release. I know the font is supposed to be a homage to the Cheetah “Sweet Talker” speech synth chip from the 80’s.</p>
        </div>
      </div>

      <div class="mock-comment">
        <img
          src="../assets/images/SebastianStanvalentino.jpeg"
          alt=""
        />
        <div class="comment-container">
          <h4>vinyllover</h4>
          <p>Great EP! It’s perfect for me, the tracks, the cover and the fact it is 2x12inch. I am a fan of 1x12 inch records cause it’s more easy to handle.</p>
        </div>
      </div>

      <div class="mock-comment">
        <img
          src="../assets/images/SebastianStanvalentino.jpeg"
          alt=""
        />
        <div class="comment-container">
          <h4>chicken</h4>
          <p>Norty track bruv</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script></script>

<style scoped lang="scss">
.comment-container {
  display: flex;

  .button-container {
    display: flex;
    justify-content: right;

    button {
      height: 44px;
      width: 224px;
      margin-top: 10px;
      background-color: black;
      color: white;
      border: none;
      font-size: 1.1em;
      cursor: pointer;
      transition: border-color 0.25s;
    }
  }

  .post-comment {
    margin-top: 30px;

    h4 {
      margin-bottom: 10px;
    }

    textarea {
      resize: none;
    }
  }

  .view-comment-container {
    display: flex;
    flex-direction: column;
    // margin-top: 30px;
    margin: 30px 0px 0px 30px;

    .mock-comment {
      display: flex;
      max-height: 60px;
      padding: 10px;
      align-items: center;

      border-bottom: 1px solid;

      .comment-container {
        display: flex;
        flex-direction: column;
      }

      img {
        margin-right: 30px;
        min-width: 60px;
        height: 60px;
        object-fit: cover;
        object-position: top;
        border-radius: 50%;
      }
    }
  }
}
</style>
