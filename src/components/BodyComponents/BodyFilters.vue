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
            <input type="checkbox" v-model="colors" value="headphones" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature4"/>
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
                Smartphones
            </label>
            </div>
        </div>
        <div class="relative flex items-center m-1">
            <input type="checkbox" v-model="colors" value="smartwatches" class="absolute top-0 left-0 opacity-0 cursor-pointer h-10 w-20" id="feature7"/>
            <div class="flex items-center justify-center transition-all px-1 duration-100 ease-in-out">
            <label for="feature7">
                Smartwatches
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
    <option value="color">Categories</option>
    <option value="size">Price</option>
  </select>
  </p>
</div>
 
    <div class="grid grid-cols-4 gap-y-10 gap-x-4 mx-20 mt-10 font-rubik">
        <div v-for="(product, index) in computedProducts" :key="index">
            <div class="flex flex-col shadow-md w-full mx-3 text-center rounded-2xl border-gray-200 hover:shadow-2xl transition-all ease-in-out duration-300">
                <img :src="product.image" alt="Denim Jeans" class="object-fill w-full rounded-2xl">
                <h1 class="text-sm text-gray-700">{{product.name}}</h1>
                <p class="text-gray-500 text-6 line-throught">{{product.size}}.00 $</p>
                <p class="capitalize">{{product.color}}</p>
                <p><button class="border-none text-white p-3 cursor-pointer text-4 w-full bg-orange rounded-b-2xl focus:outline-none hover:bg-orangeRed transition-all ease-in-out duration-300">Add to Cart</button></p>
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
        {name:'test1', color:'tvs', size:'1500', image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/32/303104/1.jpg?2319'},
        {name:'test2', color:'accessories', size:'1769', image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/00/015243/1.jpg'},
        {name:'test4', color:'cameras', size:'1897',image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/72/526753/2.jpg'},
        {name:'test5', color:'smartwatches', size:'1675', image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/21/787173/1.jpg'},
        {name:'test7', color:'laptops', size:'2098', image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/09/962114/1.jpg'},
        {name:'test6', color:'headphones', size:'3004',image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/39/231783/1.jpg?3783'},
        {name:'test6', color:'smartphones', size:'7092',image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/37/518693/1.jpg?7630'},
        {name:'Hp Pc - 8Go RAM - 500Go HDD', color:'desktops', size:'7845', image:'https://ma.jumia.is/unsafe/fit-in/680x680/filters:fill(white)/product/98/235014/1.jpg?3976'}
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
        return a[this.sortBy].localeCompare(b[this.sortBy])
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