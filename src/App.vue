<script>
import { Shoe } from "./Shoes";

export default {
  data() {
    return {
      //prettier-ignore
      shoes: [
        new Shoe(1, "Nike", "Air Structure 1", 149.95, "https://i.ibb.co/R0Y8T8r/nike19.png","https://i.ibb.co/q7RKcZk/nike.png","From the Flymesh upper to the triple-density foam midsole, the Nike Air Zoom Structure 19 Men's Running Shoe offers plenty of support and the response you need for a smooth, stable ride that feels ultra fast"),
        new Shoe(2, "New Balance", "Air Solstice QS", 265.00, "https://i.ibb.co/ZMVHp6x/nike-air-solstice.png","src/assets/img/nb.png","The Nike Air Solstice draws inspiration from the swoosh's classic running shoes of the 1980's updating the style with premium materials and impressive production quality."),
       
        // new Shoe(3, "Adidas", "f3", 240, "src/assets/img/adidas1.png"),
        new Shoe(4, "Adidas", "Air Huarache Utility", 143.50, "https://i.ibb.co/9bc3SYK/nike-safari.png","src/assets/img/adidaslogo.png","The Nike Air Huarache Utility Men's Shoe toughens up a famous running shoe with a nylon upper, fused mudguard and vibrant detail"),
      ],
      selectedBrand: "all",
    };
  },
  methods: {
    brands() {
      let result = [];
      for (const shoe of this.shoes) {
        if (result.indexOf(shoe.brand) == -1) {
          result.push(shoe.brand);
        }
      }
      return result;
    },
  },
};
</script>

<template>
  <div class="container">
    <select class="form-select" name="brand" id="" v-model="selectedBrand">
      <option value="all">Show all</option>
      <option v-for="brand in brands()" :value="brand">{{ brand }}</option>
    </select>
    <div class="row">
      <template v-for="shoe in shoes">
        <div
          v-if="shoe.brand == selectedBrand || selectedBrand == 'all'"
          class="col-md-4 my-3"
        >

          <div class="card">
            <div class="container_big_txt">
              <div class="watermark_container">
                <p class="watermark_body">{{ shoe.brand }}</p>
              </div>
            </div>
            <div class="d-flex justify-content-between container_logo_price">
              <img :src="shoe.logo" alt="logo" id="logo_header" />
              <h4 id="price_card">{{ shoe.price }}€</h4>
            </div>
            <div class="description text-start">
              <h4 class="model">{{ shoe.model }}</h4>
              {{ shoe.description }}
            </div>
            <div class="container_shoes">
              <img :src="shoe.image" class="shoes_img" alt="..." />
            </div>
            <div class="container-btn">
              <button class="btn btn-footer">Add to list</button>
            </div>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>
