<template>
  <div class="bg-gray-900 h-screen">
    <div class="flex" style="height: 100vh">
      <!-- Side nav -->
      <div class="w-56 bg-black h-full flex-none">
        <div class="">
          <img src="./assets/images/spotifyLogo.jpg" alt="">
        </div>

        <div class="mx-2">
          <button v-for="page in pages" :key="page.id" @click="setID = page.id" :class="`w-full text-sm font-semibold rounded px-3 py-2 flex items-center  text-white justify-start ${setID === page.id ? 'bg-gray-600' : ''}`">
            <i class="material-icons mr-3"> {{page.icon}} </i>
            <p>{{page.name}}</p>
          </button>
        </div>

        <div class="mx-2">
            <h1 class="cursor-pointer text-white text-lightest tracking-widest uppercase p-6">Playlists</h1>
            <button class="p-2 font-semibold opacity-75 hover:opacity-100">(+) Create Playlists</button>
            <button class="p-2 font-semibold opacity-75 hover:opacity-100">(^.^) Like Songs</button>
            <div class="h-px w-4/5 bg-gray-300 my-3"></div>
        </div>

        <div class="mx-2 mt-6">
            <p class="cursor-pointer text-white text-lightest tracking-widest uppercase p-3">Kind of music</p>
            <div class="w-full h-28 overflow-y-scroll">
              <p v-for="album in albums" :key="album" class="cursor-pointer hover:text-gray-400 text-sm py-1">{{album.name}}</p>
            </div>
            <button class='rounded mt-20 bg-red-50 text-black p-2 ml-12 '>Install App</button>
        </div>
      </div>

      <!-- Main content -->
      <div class="w-full h-full relative overflow-y-scroll">
          <!-- Header -->
          <div class="w-full sticky top-0 py-4 px-6 flex items-center justify-between bg-gray-900">
            <div class="flex items-center">
              <button class="rounded-full bg-black w-8 h-8 text-white mr-3">
                <i class="material-icons ">keyboard_arrow_left</i>
              </button>
              <button class="rounded-full bg-black w-8 h-8 text-white">
                <i class="material-icons ">keyboard_arrow_right</i>
              </button>
            </div>
            <div class="relative">
              <button @click="dropDown = true" class="bg-gray-600 rounded-full p-1 flex items-center">
                <img src="./assets/images/face.png" class="rounded-full h-6 w-6 mr-3">
                <p class="font-semibold text-xs mr-3">Tùng Alex</p>
                <i v-if="!dropDown" class="material-icons ">arrow_drop_down</i>
                <i v-else class="material-icons ">arrow_drop_up</i>
              </button>
              <div v-if="dropDown" class="absolute bg-gray-600 w-full rounded mt-1">
                <button @click="dropDown = false" class="w-full py-2 hover border-b text-sm">Account</button>
                <button @click="dropDown = false" class="w-full py-2 hover text-sm">Log Out</button>
              </div>
            </div>
          </div>
          <!-- Card -->
          <!-- Section1 -->
          <div class="px-6 py-3">
            <div class=" flex justify-between items-center">
              <h1 class="text-2xl font-semibold tracking-wider hover:underline">Recently Played</h1>
              <h2 class="text-xs uppercase tracking-wider hover:underline mb-3">See All</h2>
            </div>
            <div class="w-full flex flex-wrap">
              <div v-for="recent in recents" :key="recent" class="p-2 w-48 relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green-600 rounded-full h-10 w-10 flex items-center justify-center">
                    <i class="material-icons text-2xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-gray-600 w-full h-auto p-5 rounded-lg shadow-md">
                  <img :src="recent.src" class="h-auto w-full shadow mb-2">
                  <h1 class="text-sm font-semibold tracking-wide mb-2">{{recent.title}}</h1>
                  <h2 class="text-xs tracking-wide mb-3">{{recent.artist}}</h2>
                </div>
              </div>
            </div>
          </div>
          <!-- Section 2 -->
          <div class="px-6 py-3">
            <div class="">
              <h1 class="text-2xl font-semibold tracking-wider hover:underline">Made For Stephaniw</h1>
              <h2 class="text-sm tracking-wider mb-3 ">Get better recommentdations the more you listen </h2>
            </div>
            <div class="w-full flex flex-wrap">
              <div v-for="stephan in stephans" :key="stephan" class="p-2 w-48 relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green-600 rounded-full h-10 w-10 flex items-center justify-center">
                    <i class="material-icons text-2xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-gray-600 w-full h-auto p-5 rounded-lg shadow-md">
                  <img :src="stephan.src" class="h-auto w-full shadow mb-2">
                  <h1 class="text-sm font-semibold tracking-wide mb-2">{{stephan.title}}</h1>
                  <h2 class="text-xs tracking-wide mb-3">{{stephan.artist}}</h2>
                </div>
              </div>
            </div>
          </div>
          <!-- Section 3 -->
                    <div class="px-6 py-3">
            <div class="">
              <h1 class="text-2xl font-semibold tracking-wider hover:underline">Made For Stephaniw</h1>
              <h2 class="text-sm tracking-wider mb-3 text-gray-400">Get better recommentdations the more you listen </h2>
            </div>
            <div class="w-full flex flex-wrap">
              <div v-for="stephan in stephans" :key="stephan" class="p-2 w-48 relative">
                <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                  <div class="bg-green-600 rounded-full h-10 w-10 flex items-center justify-center">
                    <i class="material-icons text-2xl">play_arrow</i>
                  </div>
                </div>
                <div class="bg-gray-600 w-full h-auto p-5 rounded-lg shadow-md">
                  <img :src="stephan.src" class="h-auto w-full shadow mb-2">
                  <h1 class="text-sm font-semibold tracking-wide mb-2">{{stephan.title}}</h1>
                  <h2 class="text-xs tracking-wide mb-3">{{stephan.artist}}</h2>
                </div>
              </div>
            </div>
          </div>
      </div>
    </div>
    <!-- play bar -->
    <div class="w-full flex items-center justify-between px-3 bg-gray-800 " style="height: 12vh">
      <div class="flex items-center">
        <div>
          <h1 class="mb-1 text-sm tracking-wide">Mình yêu nhau bình yên thôi</h1>
          <h2 class="text-xs tracking-wide">Hà Anh Tuấn</h2>
        </div>
        <i class="material-icons text-base text-green-600 mx-4">favorite</i>
        <i class="material-icons text-2xl text-gray-400 hover:text-white">picture_in_picture_alt</i>
      </div>
      <div class="flex flex-col justify-center w-1/3 items-center">
        <div class="flex items-center">
          <button class="mx-3">
            <i class="material-icons text-gray-400 hover:text-white">shuffle</i>
          </button>
          <button class="">
            <i class="material-icons text-gray-400 hover:text-white">skip_previous</i>
          </button>
          <button class="rounded-full h-10 w-10 mx-3 mb-2 border-gray-400 border flex items-center justify-center">
            <i class="material-icons text-gray-400 hover:text-white">play_arrow</i>
          </button>
          <button class="">
            <i class="material-icons text-gray-400 hover:text-white">skip_next</i>
          </button>  
          <button class="mx-3">
            <i class="material-icons text-gray-400 hover:text-white">repeat</i>
          </button>                  
        </div>
        <div class="w-full">
          <div class="w-full h-2 bg-black rounded-full mt-4 flex items-center">
            <div class="h-2 bg-green-600 rounded-full" style="width: 50%">
            
            </div>
            <div class="h-3 w-3 bg-white rounded-full -ml-1 shadow"></div>
          </div>
        </div>
      </div>
      <div class="flex item-center">
        <i class="material-icons text-gray-400 hover:text-white">playlist_play</i>
        <i class="material-icons mx-3 text-gray-400 hover:text-white" >important_devices</i>
        <i class="material-icons text-gray-400 hover:text-white">volume_up</i>
        <div class="w-20 ml-1 mt-3 bg-gray-400 rounded-full h-1 hover:bg-white"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      pages: [
        {id: "home", name: "Home", icon:"home" },
        {id: "search", name: "Search", icon:"search" },
        {id: "library", name: "Your Library", icon:"bar_chart" },
      ],
      setID: 'home',
      albums: [
        {name:'Frive'},
        {name:'Zhu'},
        {name:'Funny'},
        {name:'All new indie'},
        {name:'ClassSic'},
        {name:'Gold Music'},
        {name:'Rock'},
        {name:'MTP'},
      ],
      dropDown: false,
      recents: [
        {src:require("./assets/images/face.png"), title:'At My Worst', artist: 'Pink Pick'},
        {src:require("./assets/images/face.png"), title:'Lối Nhỏ', artist: 'Đen Vâu'},
        {src:require("./assets/images/face.png"), title:'The Nights', artist: 'Avicii'},
        {src:require("./assets/images/face.png"), title:'Big CityBoy', artist: 'Binz'},
        {src:require("./assets/images/face.png"), title:'Có chắc yêu là đây', artist: 'Sơn Tùng MTP'},
        {src:require("./assets/images/face.png"), title:'Thanh Xuân ', artist: 'Da lab'},
      ],
      stephans: [
        {src:require("./assets/images/face.png"), title:'Mình yêu nhau bình yên thôi', artist: 'Hà Anh Tuấn'},
        {src:require("./assets/images/face.png"), title:'Ngày khác lạ rủ nhau đi trốn', artist: 'Đen Vâu'},
        {src:require("./assets/images/face.png"), title:'Dấu những cơn mưa', artist: 'HKT'},
        {src:require("./assets/images/face.png"), title:'Dưới những cơn mưa', artist: 'Mr.Siro'},
        {src:require("./assets/images/face.png"), title:'Ngày chưa giông bão', artist: 'Hồ Xuân Hương'},
        {src:require("./assets/images/face.png"), title:'Yêu rất nhiều người khác lạ', artist: 'Min'},
      ],
    }
  },
  methods: {

  },
  created() {
   
  },
};
</script>

<style>
*{
  color: #fff;
}
</style>
