<template>
  <div class="relative">
      <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i" class="h-1/2 overflow-hidden">
        <img :src="currentImg" class="object-cover h-96 w-full" id="slice" />
        <div class="absolute top-1/4 left-24 grid space-y-4 font-rubik w-96">
        <p class="text-white bg-black bg-opacity-5 w-32 px-3 py-2">{{currentCaption.text1}}</p>
        <span class="text-5xl text-white bg-black bg-opacity-5 px-3 py-2">{{currentCaption.text2}}</span>
        <button class="bg-orange p-3 text-white text-sm rounded-md w-32">Get in touch</button>
        </div>
      </div>
    </transition-group>
    <a class="cursor-pointer absolute top-0 right-16 w-auto py-2 px-5 text-white font-bold text-sm transition-all duration-700 ease bg-orangeRed hover:bg-black z-10" @click="prev" href="#">&#10094;</a>
    <a class="cursor-pointer absolute top-0 right-3 w-auto py-2 px-5 text-white font-bold text-sm transition-all duration-700 ease bg-orangeRed hover:bg-black z-10" @click="next" href="#">&#10095;</a>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
        "https://images.unsplash.com/photo-1509695507497-903c140c43b0?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=752&q=80",
        "https://images.unsplash.com/3/www.madebyvadim.com.jpg?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1361&q=80",
        "https://images.unsplash.com/photo-1601924638867-3a6de6b7a500?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
      ],
      captions:[
          {id:1,
          text1:'Summer Sale',
          text2:'50% Off everything!',
          },
          {id:2,
          text1:'A luxury',
          text2:'That everyone can offord',
          },
          {id:3,
          text1:'Best Product',
          text2:'We offer you the best products',
          },
      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    //this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 9000);
    },

    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    },
    currentCaption: function() {
      return this.captions[Math.abs(this.currentIndex) % this.captions.length];
    }
  }
};
</script>

<style scoped>
.fade-enter-active {
  animation: fade-in 0.5s;
  width: 100%;
  height: auto;
}
.fade-leave-active {
  animation: fade-in 0.5s reverse;
  width: 100%;
  height: auto;
  position: absolute;
}

@keyframes fade-in {
  0% {
    transform: scale(0);
  }
  
  100% {
    transform: scale(1);
  }
}
</style>