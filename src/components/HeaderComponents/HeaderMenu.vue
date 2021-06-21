<template>
 <div class="flex justify-between p-4 border-b items-center space-x-3 px-28">
   <div class="flex space-x-2">
     <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z" />
    </svg>
    <span class="text-charade">
      Chips
    </span>
   </div>
   <div class="hidden md:flex justify-between space-x-5 font-rubik">
     <ul class="flex space-x-4 items-center">
        <li><a href="#">Home</a></li>
        <li><a href="#">Product</a></li>
        <li><a href="#">Offer</a></li>
        <li><a href="#">New Arrival</a></li>
      </ul>
   </div>
   <div class="flex items-center justify-between space-x-4">
     <div class="flex items-center relative">
       <input type="text" name="search" class="py-2 border border-gray-100 bg-gray-50 rounded-full focus:outline-none w-full pl-5 pr-10 text-sm" v-model="search" />
       <svg xmlns="http://www.w3.org/2000/svg" viewBox="-2.5 -2.5 24 24" @click="trigger" preserveAspectRatio="xMinYMin" class="icon__icon w-6 h-6 absolute right-2"><path d="M8 14A6 6 0 1 0 8 2a6 6 0 0 0 0 12zm6.32-1.094l3.58 3.58a1 1 0 1 1-1.415 1.413l-3.58-3.58a8 8 0 1 1 1.414-1.414z"></path></svg>
     </div>
     <div class="flex items-center space-x-5">
        <notification>
          <template v-slot:icon>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="-2 -4 24 24" preserveAspectRatio="xMinYMin" class="icon__icon w-6 h-6 cursor-pointer"><path d="M3.636 7.208L10 13.572l6.364-6.364a3 3 0 1 0-4.243-4.243L10 5.086l-2.121-2.12a3 3 0 0 0-4.243 4.242zM9.293 1.55l.707.707.707-.707a5 5 0 1 1 7.071 7.071l-7.07 7.071a1 1 0 0 1-1.415 0l-7.071-7.07a5 5 0 1 1 7.07-7.071z"></path></svg>
          </template>
          <template v-slot:highlight>
            <span class="text-xs text-white font-semibold">3</span>
          </template>
          <template v-slot:dropdown>
            <ul class="flex w-52">
              <li class="flex flex-grow">
                <div class="px-4 py-3">
                  <span class="text-sm"><a href="#" class="font-semibold hover:text-green-light">John Doe</a> liked your post</span>
                </div>
              </li>
            </ul>
          </template>
        </notification>
        <notification>
          <template v-slot:icon>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="-3 -4 24 24" preserveAspectRatio="xMinYMin" class="icon__icon w-6 h-6 cursor-pointer"><path d="M7 16a2 2 0 1 1 0-4 2 2 0 0 1 0 4zm7 0a2 2 0 1 1 0-4 2 2 0 0 1 0 4zM.962 1.923A.962.962 0 0 1 .962 0h1.151c.902 0 1.682.626 1.878 1.506l1.253 5.642c.196.88.976 1.506 1.878 1.506h7.512l1.442-5.77H6.731a.962.962 0 0 1 0-1.922h9.345a1.923 1.923 0 0 1 1.866 2.39L16.5 9.12a1.923 1.923 0 0 1-1.866 1.457H7.122a3.846 3.846 0 0 1-3.755-3.012L2.113 1.923H.962z"></path></svg>
          </template>
          <template v-slot:highlight>
            <span class="text-xs text-white font-semibold">6</span>
          </template>
          <template v-slot:dropdown>
            <ul class="flex w-52">
              <li class="flex flex-grow">
                <div class="px-4 py-3">
                  <span class="text-sm"><a href="#" class="font-semibold hover:text-green-light">John Doe</a> liked your post</span>
                </div>
              </li>
            </ul>
          </template>
        </notification>
       <div class="flex text-sm font-rubik">
        <span class="text-gray-600">Total Price : </span>
        <span class="font-bold "> 150.0 $</span>
       </div>
     </div>
   </div>

   <div class="md:hidden">
     <div class="relative">
       <button class="focus:outline-none" @click="toggle">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-charade" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" />
        </svg>
       </button>
     </div>
    <div v-if="isOpen" class="absolute left-0 mt-4 flex flex-col space-y-7 p-3 shadow-md text-sm font-rubik w-full border">
      <ul class="flex flex-col space-y-5">
        <li><a href="#">Home</a></li>
        <li><a href="#">Product</a></li>
        <li><a href="#">Offer</a></li>
        <li><a href="#">New Arrival</a></li>
      </ul>
      <button class="bg-orange py-2 px-3 rounded-lg shadow text-sm text-white focus:outline-none">Contact</button>
    </div>
   </div>
 </div>
</template>

<script>
import Notification from '../ReusableComponents/Notification.vue';
export default {
  name: 'Menu',
  components:{
    'notification' :Notification
  },
  data(){
    return{
      isOpen:false,
      search:''
    }
  },
  methods:{
    toggle(){
      this.isOpen = !this.isOpen
    },
  }
}
</script>

<style scoped>
</style>
