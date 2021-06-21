<template>
  <!-- <p><strong>Keyword:</strong>
  <input type="text" class="border" v-model="keyword"></p> -->
<div class="flex justify-between mx-20">
    <div class="flex items-center">
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="accessories" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature1"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature1">
                Accessories
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="cameras" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature2"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature2">
                Cameras
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="desktops" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature3"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature3">
                Desktops
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="headphnes" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature4"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature4">
                Headphones
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="laptops" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature5"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature5">
                Laptops
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="smartphones" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature6"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature6">
                SmartPhones
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="smartwatches" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature7"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature7">
                SmartWatches
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="tvs" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature8"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature8">
                TVs
            </label>
            </div>
        </div>
  </div>
    <p><strong>Sort By:</strong> <select v-model="sortBy" class="bg-gray-200 text-black p-2 focus:outline-none">
    <option value="name">Product Name</option>
    <option value="color">Color</option>
    <option value="size">Size</option>
  </select>
  </p>
</div>
 
    <div class="grid grid-cols-3 gap-4 mx-20 rounded-2xl mt-10">
        <div class="rounded-2xl" v-for="(product, index) in computedProducts" :key="index">
            <div class="flex flex-col shadow-md w-full mx-3 text-center">
                <img :src="product.image" alt="Denim Jeans" class="object-fill w-full h-full">
                <h1>{{product.name}}</h1>
                <p class="text-gray-500 text-6">{{product.size}}</p>
                <p>{{product.color}}</p>
                <p><button class="border-none text-white p-3 cursor-pointer text-4 w-full bg-black focus:outline-none hover:opacity-70">Add to Cart</button></p>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    
 data() {
    return {
      colors: [],
      sizes: [],
      products: [
        {name:'test1', color:'tvs', size:'XL', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test2', color:'accessories', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test3', color:'tvs', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test4', color:'cameras', size:'XL',image:'https://ipt.imgix.net/206731/x/0/5-types-of-cameras-digital.jpg?w=860&h=480&fit=crop&dpr=2&auto=format%2C%20compress&ixlib=react-8.6.4'},
        {name:'test5', color:'smartwatches', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test6', color:'smartphones', size:'XL',image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test7', color:'laptops', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test6', color:'smartphones', size:'XL',image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test7', color:'laptops', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test6', color:'smartphones', size:'XL',image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test7', color:'laptops', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test6', color:'smartphones', size:'XL',image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test7', color:'laptops', size:'L', image:'https://demo420.nopcommerce.pl/images/thumbs/0000024_apple-macbook-pro-13-inch_550.jpeg'},
        {name:'test7', color:'desktops', size:'L', image:'https://www.hp.com/us-en/shop/app/assets/images/uploads/prod/best-10-hp-desktops-for-everyday-use-21552526779305.png?impolicy=prdimg&imdensity=1&imwidth=600'}
      ],
      sortBy: 'name',
      keyword: ''
    }
  },
  computed: {
    computedProducts: function () {
      return this.products.filter((item) => {
        return (this.keyword.length === 0 || item.name.includes(this.keyword)) &&
        (this.colors.length === 0 || this.colors.includes(item.color)) &&
        (this.sizes.length === 0 || this.sizes.includes(item.size))
      }).sort((a, b) => {
        return a[this.sortBy].toString().localeCompare(b[this.sortBy].toString())
      })
    }
  }
}
</script>

<style scoped>

input[type=checkbox]:checked ~ div {
  border-bottom: 2px solid #ff4500;
}

</style>