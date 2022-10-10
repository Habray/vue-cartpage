<template>
    <!-- <div>
      <ul v-for="post in posts" v-bind:key="post.id">
        <li>{{ post.title }}</li>
        <p>{{ post.body }}</p>
      </ul>
    </div> -->
    
    <div class="cards" v-for="post in posts" v-bind:key="post.id">
        <div class="card" style="width: 18rem;">
        <img class="card-img-top" :src="post.image" alt="Card image cap">
            <div class="card-body">
                <h5 class="card-title">{{post.title}}</h5>
                <p class="card-text text-primary">$ {{post.price}}</p>
                <a href="#" class="btn btn-primary">Add to Card</a>
            </div>
        </div>
    </div>
</template>
  
<script>
  export default {
    data() {
      return {
        posts: [],
      };
    },
  
    methods: {
      async getData() {
        try {
          let response = await fetch("https://fakestoreapi.com/products");
          this.posts = await response.json();;
        } catch (error) {
          console.log(error);
        }
      },
    },
  
    created() {
      this.getData();
    },
  };
</script>

<style scoped>
    .card {
        margin: 10px;
    }
    /* .card-img-top {
        object-fit: cover;
        height: 100px;
        width: 80px;
    } */
    a {
        text-decoration: none;
    }
    .card-title {
        color: #484848;
    }
</style>