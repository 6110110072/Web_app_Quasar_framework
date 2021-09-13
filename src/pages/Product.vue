<template>
  <div class="q-pa-md">
    <div class="row" style="padding: 15px">
      <div
        class="col"
        style="margin: 15px"
        v-for="product in products1"
        :key="product.name"
      >
        <q-card class="my-card">
          <img
            :src="product.image"
            style="width: 100%; height: auto; max-height: 300px"
          />

          <q-card-section>
            <div class="text-h6">{{ product.name }}</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ product.desc }}
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="row" style="padding: 15px">
      <div
        class="col"
        style="margin: 15px"
        v-for="product in products2"
        :key="product.name"
      >
        <q-card class="my-card">
          <img :src="product.image" style="width: 100%" />

          <q-card-section>
            <div class="text-h6">{{ product.name }}</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ product.desc }}
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      products1: [
        {
          name: "T-shirt",
          image:
            "https://cf.shopee.co.th/file/6c1d5eebf76156d1a7de522eaafe3674",
          desc: "Peaky Blinders Amazing T Shirts Brand New Cotton Fabric Clothing Father Day O Neck Pure Cotton Fitness Tops Shirts Summer Tshirt",
        },
        {
          name: "Chocolate cookies",
          image:
            "https://cf.shopee.co.th/file/eacbf4d2c921beca32182528564f4cf0",
          desc: "“Ultimate Chocolate Chip Cookies,” because it’s got everything a cookie connoisseur could possibly ask for. With a texture that is slightly crispy",
        },
        {
          name: "Cat food",
          image:
            "https://cf.shopee.co.th/file/e4872a175bd14a37df1abfb970ed3ea9",
          desc: "Description Dinner is served with the Fancy Feast Classic Seafood Feast Variety Pack. With a delicious combo of all your cat’s favorite seafood flavors",
        },
      ],
      products2: [
        {
          name: "Apple pencil silicone case cover",
          image:
            "https://cf.shopee.co.th/file/601a4cbf657b052b8823b898992ee634",
          desc: "Silicone Case Multiple colors For Apple Pencil gen 1 Cradle Stand Holder For iPad Pro Stylus Pen Protective Cover",
        },
        {
          name: "Wireless Mouse",
          image:
            "https://cf.shopee.co.th/file/c82a3b1647c9934c2a70df465072e011",
          desc: "Extensive arsenal of high-performance gaming mouse - wired or wireless mouse, FPS, MMO or MOBA gaming mouse, left-handed mouse",
        },
        {
          name: "Monstera delisiosa",
          image:
            "https://cdn.shopify.com/s/files/1/0059/8835/2052/products/Monstera_delisiosa_4_FGT_650x.jpg?v=1612444295",
          desc: "Monstera deliciosa, the Swiss cheese plant, is a species of flowering plant native to tropical forests of southern Mexico, south to Panama",
        },
      ],
    };
  },
});
</script>
