<template>
  <div
    v-if="record"
    class="product-details-container"
  >
    <div class="record-image-wrapper">
      <img
        :src="record.imageUrl"
        alt="Record cover"
        class="record-image"
      />
    </div>

    <div class="product-details">
      <h1 class="record-album">{{ record.albumTitle }}</h1>

      <div class="product-titles ">
        <h4 class="column-1">ARTIST</h4>
        <p class="record-artist column-2">{{ record.artistName }}</p>
      </div>

      <div class="product-titles">
        <h4 class="column-1">LABEL</h4>
        <p class="column-2">Details for Label here?</p>
      </div>

      <div class="product-titles">
        <h4 class="column-1">COUNTRY</h4>
        <p class="column-2">Details for Country here?</p>
      </div>

      <div class="product-titles">
        <h4 class="column-1">RELEASED</h4>
        <p class="record-year column-2">{{ record.yearReleased }}</p>
      </div>

      <div class="product-titles">
        <h4 class="column-1">GENRE</h4>
        <p class="record-genre column-2">{{ record.genre }}</p>

        <!-- <p class="record-genre" v-for="(genre, index) in vinyls.genre" :key="index">{{ genre }}</p> -->
      </div>

      <div class="product-titles">
        <h4 class="column-1">FORMAT</h4>
        <p class="record-length column-2">{{ record.length }}</p>
      </div>

      <div>
        <p>
          Cheetah is an EP record by British electronic musician Richard D. James, released under his moniker Aphex Twin. According to Wikipedia “The name is a reference to Cheetah Marketing, a British manufacturer of microcomputer peripherals and electronic musical instruments in the 1980s (such as
          the MS800 namechecked in two of the EP’s track titles).”
        </p>
      </div>

      <div class="icon-container">
        <svg-icon
          type="mdi"
          :path="path"
        ></svg-icon>
      </div>

      <div class="button-container">
        <div>
          <h2 class="record-price">${{ record.price }}.00</h2>
        </div>
        <!-- <button class="edit">EDIT</button> -->
        <button class="purchase">PURCHASE</button>
      </div>
    </div>
  </div>

  <div>
    <CommentSection />
  </div>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon'
// import { mdiAccount } from '@mdi/js'
import { mdiHeartOutline } from '@mdi/js'

import ProductService from '../services/ProductService.js'
import CommentSection from '../components/CommentSection.vue'

export default {
  props: ['id'],
  data() {
    return {
      record: null,
      path: mdiHeartOutline,
    }
  },
  components: {
    SvgIcon,
    CommentSection,
  },
  created() {
    ProductService.getData(this.id)
      .then(response => {
        // console.log(response.data);
        this.record = response.data
      })
      .catch(error => {
        console.log(error)
      })
  },
}
</script>

<style lang="scss" scoped>
.product-details-container {
  display: flex;
  border-bottom: 1px solid;

  .product-details {
    display: flex;
    flex-direction:column;
    margin-bottom: 2rem;

    .column-1 {
    min-width: 100px;
    display: flex;
  }
  // .column-2 {
  //   text-align: right;
  // }

    h1 {
      margin: 2rem 0rem ;
    }

    .product-titles {
      display: flex;
      margin-bottom: 25px;

      h4 {
        margin-right: 0px;
      }

      .record-artist {
        font-style: italic;
        font-weight: 800;
      }

      .record-length {
        text-transform: uppercase;
      }
    }
  }

  //image styling
  .record-image-wrapper {
    .record-image {
      height: 476px;
      margin: 2rem 2rem 2rem 0rem;
    }
  }

  .icon-container {
    display: flex;
    justify-content: right;
  }

  //button styling - can be moved to main.scss
  .button-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    button {
      height: 44px;
      width: 224px;
      margin: 5px;
      background-color: black;
      color: white;
      border: none;
      font-size: 1.1em;
      cursor: pointer;
      transition: border-color 0.25s;
    }
  }
}
</style>
