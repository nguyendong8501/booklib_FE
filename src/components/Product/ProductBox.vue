<template>
  <div class="card h-100 w-80">
    <router-link :to="{ name: 'ShowDetails', params: { id: product.id } }">
    <div class="embed-responsive embed-responsive-16by9">
      <img
        class="card-img-top embed-responsive-item"
        :src="product.imageURL"
        alt="Product Image"
      />
    </div>
  </router-link>
    <div class="card-body">
      <router-link :to="{ name: 'ShowDetails', params: { id: product.id } }"
        ><h5 class="card-title">{{ product.name }}</h5></router-link
      >
      <p class="card-text">{{ product.price }}<sup> VND</sup></p>
      <p class="card-text font-italic">
        {{ product.description.substring(0, 65) }}...
      </p>
      <router-link
        id="edit-product"
        :to="{ name: 'EditProduct', params: { id: product.id } }"
        v-show="$route.name == 'AdminProduct'"
      >
        Sửa
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductBox",
  props: ["product"],
  methods: {
    showDetails() {
      this.$router.push({
        name: "ShowDetails",
        params: { id: this.product.id },
      });
    },
  },
};
</script>

<style scoped>
.embed-responsive .card-img-top {
  /* object-fit: cover; */
  height:340px;
}
/* .embed-responsive{
  position: relative;
display: block;
width: 100%;
padding: 0px;
overflow: hidden;
height: 340px;
} */
/* .embed-responsive .embed-responsive-16by9 ::before{
  padding-top: 150%;
} */
a {
  text-decoration: none;
}

.card-title {
  color: #484848;
  font-size: 1.1rem;
  font-weight: 400;
}

.card-title:hover {
  font-weight: bold;
}

.card-text {
  font-size: 1.0rem;
}

#edit-product {
  float: right;
}
</style>
