<template>
<div class="home">

<div class="pure-menu pure-menu-horizontal">
<ul class="pure-menu-list">
<li class="pure-menu-item"><a @click="select('Dress')" href="#" class="pure-menu-link">Dresses</a></li>
<li class="pure-menu-item"><a @click="select('Shirt')" href="#" class="pure-menu-link">Shirts</a></li>
<li class="pure-menu-item"><a @click="select('Hat')" href="#" class="pure-menu-link">Hats</a></li>
<li class="pure-menu-item"><a @click="select('Custom')" href="#" class="pure-menu-link">Custom Designs</a></li>
</ul>
</div>

  <section class="image-gallery">

    <div class="image" v-for="item in sortItems(items)" :key="item.id">
      <h2>{{item.title}}</h2>
      <div class="creator">
      <h3>By</h3>
      <h3></h3>
      <h3> {{item.user}}</h3>
      </div>
      <p> {{item.code}}</p>
      <img :src="item.path" />
    </div>
  </section>
</div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'Home',

    data() {
    return {
     items: [],
     type:"",
    }
  },
    created() {
    this.getItems();
  },
    methods: {
    select(type) {
      this.type = type;
    },
    sortItems(items) {
      return items.filter(item => item.type === this.type)
    },
    async getItems() {
      try {
        let response = await axios.get("/api/items");
        this.items = response.data;
        return true;
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>

<style scoped>
.image h2 {
  font-style: italic;
  font-size: 20px;
}

.image h3 {
  font-size: 15px;
  display: flex;
  justify-content: center;
  margin: 0 auto;
}

.pure-menu-list {
  display: flex;
  align-items: center;
  justify-content: space-around;
  list-style-type: none;
}

.creator {
  display: flex;
  justify-content: space-around;
  width: 25%;
  margin: 0 auto;
}

.pure-menu-link {
  text-decoration: none;
  color: #305C80;
  font-size: 20px;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 1.5em;
}

.image {
  margin: 0 0 1.5em;
  display: inline-block;
  width: 100%;
  position: relative;
}

.image:hover img {
  opacity: .25;
  transition: .5s ease;
}

.image img {
  width: 100%;
}

.image p {
  opacity: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-45%, -45%);
  margin: 0 auto;
  font-size: 20px;
  color: black;
  font-weight: bold;
}
.image:hover p {
  opacity: 1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-45%, -45%);
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 4;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 3;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 2;
  }
}
</style>
