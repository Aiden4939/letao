<script setup lang="ts">
// import Swiper core and required modules
import {
  Autoplay,
  Pagination,
  Navigation,
  EffectCoverflow,
} from "swiper/modules";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "swiper/css/scrollbar";
import { ref, reactive } from "vue";
import BottomMenu from "./BottomMenu.vue";

interface ListType {
  id: number;
  name?: string | undefined;
  src?: string | undefined;
}

const itemList: ListType[] = [
  { id: 118, name: "幼兒服裝、鞋" },
  { id: 119, name: "包、雙背帶書包" },
  { id: 120, name: "出生賀禮、紀念品" },
  { id: 121, name: "兒童家具" },
  { id: 122, name: "兒童自行車、三輪車" },
  { id: 123, name: "玩具、教材" },
  { id: 124, name: "紀念、儀式用品" },
  { id: 125, name: "衛生用品、健康護理" },
  { id: 126, name: "餵奶、產後服裝" },
  { id: 127, name: "餵奶用品" },
  { id: 128, name: "背巾" },
  { id: 129, name: "浴室、洗浴用品" },
  { id: 130, name: "其他嬰幼兒、孕婦用品" },
  { id: 131, name: "基本化妝" },
  { id: 132, name: "女士護髮" },
  { id: 133, name: "套組" },
  { id: 134, name: "化妝" },
  { id: 135, name: "化妝工具" },
  { id: 136, name: "睫毛用品" },
  { id: 137, name: "美體護理" },
  { id: 138, name: "男士刮臉用品" },
  { id: 139, name: "男士護髮" },
  { id: 140, name: "男士護膚、化妝" },
  { id: 141, name: "香水" },
  { id: 142, name: "護膚" },
  { id: 143, name: "護膚、基礎化妝品" },
  { id: 144, name: "防曬" },
  { id: 145, name: "脫毛、除毛" },
  { id: 146, name: "止汗香體劑、除臭劑" },
  { id: 147, name: "指甲" },
  { id: 148, name: "印表機、多功能事務機" },
  { id: 149, name: "平板電腦" },
  { id: 150, name: "筆電" },
  { id: 151, name: "顯示器、監視器" },
  { id: 152, name: "軟體" },
  { id: 153, name: "電源供應" },
  { id: 154, name: "PC周邊設備" },
  { id: 155, name: "PC零件" },
  { id: 156, name: "sim 卡" },
  { id: 157, name: "桌上型電腦" },
  { id: 158, name: "手機" },
  { id: 159, name: "手機、平板、配件" },
  { id: 160, name: "智能手錶、可穿戴裝置" },
  { id: 161, name: "智能手機" },
  { id: 162, name: "其他" },
  { id: 163, name: "相機" },
  { id: 164, name: "語音機器" },
  { id: 165, name: "電視機、映像機器" },
  { id: 166, name: "望遠鏡、光學機器" },
  { id: 167, name: "健康家電" },
  { id: 168, name: "廚房電器" },
  { id: 169, name: "冷暖氣器具、冷氣家電" },
  { id: 170, name: "美容家電" },
  { id: 171, name: "生活家電" },
  { id: 172, name: "資訊家電" },
  { id: 173, name: "電池、電池充電器" },
  { id: 174, name: "皮划艇、划船競賽、小船" },
  { id: 175, name: "玩樂船、遊艇" },
  { id: 176, name: "釣魚" },
  { id: 177, name: "戶外、露營、登山" },
  { id: 178, name: "海外土特產" },
  { id: 179, name: "旅行用品" },
  { id: 180, name: "其他戶外用品" },
  { id: 181, name: "健身、訓練" },
  { id: 182, name: "壘球" },
  { id: 183, name: "乒乓球" },
  { id: 184, name: "單板滑雪" },
  { id: 185, name: "籃球" },
  { id: 186, name: "網球" },
  { id: 187, name: "緊身衣物" },
  { id: 188, name: "羽球" },
  { id: 189, name: "瑜伽、普拉提斯" },
  { id: 190, name: "田徑、卡車、場" },
  { id: 191, name: "馬拉松、跑步" },
  { id: 192, name: "高爾夫球" },
  { id: 193, name: "體育器具、用品" },
  { id: 194, name: "體育看護用品" },
  { id: 195, name: "體育用內衣(通用)" },
  { id: 196, name: "體育飾品" },
  { id: 197, name: "體育／機能型包包" },
  { id: 198, name: "體操" },
  { id: 199, name: "足球、室內足球" },
  { id: 200, name: "舞蹈、芭蕾舞" },
  { id: 201, name: "排球" },
  { id: 202, name: "棒球" },
  { id: 203, name: "橄欖球" },
  { id: 204, name: "武藝、格鬥" },
  { id: 205, name: "游泳" },
  { id: 206, name: "滑雪" },
  { id: 207, name: "滑板、滑板鞋、滑板車" },
  { id: 208, name: "海上運動" },
  { id: 209, name: "其他的比賽大項" },
  { id: 210, name: "卡牌遊戲" },
  { id: 211, name: "季節玩具" },
  { id: 212, name: "乘用玩具" },
  { id: 213, name: "交換卡" },
  { id: 214, name: "圍棋、象棋、麻將" },
  { id: 215, name: "公仔" },
  { id: 216, name: "玩具" },
  { id: 217, name: "聚會商品" },
  { id: 218, name: "遙控" },
  { id: 219, name: "食玩、隨餐附贈玩具" },
  { id: 220, name: "飛鏢" },
  { id: 221, name: "電視遊戲" },
  { id: 222, name: "桌上遊戲" },
  { id: 223, name: "模型、塑膠模型" },
  { id: 224, name: "模型車" },
  { id: 225, name: "撞球" },
  { id: 226, name: "拼圖" },
  { id: 227, name: "其他玩具" },
  { id: 228, name: "自行車" },
  { id: 229, name: "汽車" },
  { id: 230, name: "摩托車" },
];

const serviceList: ListType[] = [
  {
    id: 1,
    name: "外箱更換紙袋",
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/common/icon/yahoojp/ic_01.png",
  },
  {
    id: 2,
    name: "銀鐵壺測漏水",
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/common/icon/yahoojp/ic_02.png",
  },
  {
    id: 3,
    name: "精品鑑定服務",
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/common/icon/yahoojp/ic_03.png",
  },
  {
    id: 4,
    name: "輪框拆除輪胎",
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/common/icon/yahoojp/ic_04.png",
  },
  {
    id: 5,
    name: "加強包裝服務",
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/common/icon/yahoojp/ic_05.png",
  },
];

const buyList: ListType[] = [
  { id: 1, name: "日本Yahoo拍賣" },
  { id: 2, name: "美國ebay拍賣" },
  { id: 3, name: "日本樂天" },
  { id: 4, name: "mercari" },
  { id: 5, name: "日本Yahoo購物" },
  { id: 6, name: "Rakuten Rakuma" },
  { id: 7, name: "日本Amazon" },
  { id: 8, name: "日本家電館" },
  { id: 9, name: "購物攻略" },
];

const swiperImg: ListType[] = [
  {
    id: 1,
    src: "https://letaoimg.s3.ap-northeast-1.amazonaws.com/events/20240701_mgm/web_mainbn.jpg?t=1719284433",
  },
  {
    id: 2,
    src: "https://letaoimg.s3-ap-northeast-1.amazonaws.com/events/20240701_air/web_mainbn.jpg?t=1719374211",
  },
  {
    id: 3,
    src: "https://letaoimg.s3.ap-northeast-1.amazonaws.com/events/20240701_zingala/web_mainbn.jpg?t=1719364957",
  },
];

// const onSwiper = (swiper) => {
//   console.log(swiper);
// };
// const onSlideChange = () => {
//   console.log("slide change");
// };
const modules = [Autoplay, Pagination, Navigation, EffectCoverflow];
</script>

<template>
  <!-- Header -->
  <header class="">
    <!-- Header上半部 -->
    <div
      class="top flex-row d-flex justify-content-between align-items-center px-3"
    >
      <div class="menu-btn"><i class="fa-solid fa-bars"></i></div>
      <div class="search">
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
        />
      </div>
      <div class="reload"><i class="fa-solid fa-rotate-right"></i></div>
    </div>
    <!-- Header下半部 -->
    <div
      class="bottom d-flex flex-row flex-nowrap overflow-auto align-items-center p-2"
    >
      <BottomMenu
        v-for="item in buyList"
        :key="item.id"
        :id="item.id"
        :name="item.name"
      />
    </div>
  </header>
  <!-- 主要內容 -->
  <main>
    <!-- 輪播牆 -->
    <swiper
      :slidesPerView="1"
      :spaceBetween="2"
      :pagination="{
        clickable: true,
      }"
      :centeredSlides="true"
      :loop="true"
      :autoplay="{
        delay: 2500,
        disableOnInteraction: false,
      }"
      :modules="modules"
      class="mySwiper"
    >
      <swiper-slide v-for="s in swiperImg"
        ><img :key="s.id" :src="s.src" alt=""
      /></swiper-slide>
    </swiper>
    <!-- 各種橫向商品 -->
    <div class="scroll-items d-flex flex-row">
      <!-- <div v-for="s in serviceList" :key="s.id">
        <img :src="s.src" alt="" />
      </div> -->
      <div v-for="s in serviceList" :key="s.id" class="w-25">
        <div class="card" style="">
          <img :src="s.src" class="card-img-top" alt="..." />
          <div class="card-body">
            <p class="card-text text-center small-font">
              {{ s.name }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </main>
  <!-- Footer -->
  <footer>footer</footer>
</template>

<style scoped lang="scss">
header {
  background-color: #ffffff00;

  .top {
    background-color: #fbd4ff;
    width: 100%;
    display: flex;

    .menu-btn {
    }
  }
  .bottom {
    background-color: #ecffd7;
    -ms-overflow-style: none; /* IE and Edge */
    scrollbar-width: none; /* Firefox */
  }
  .bottom::-webkit-scrollbar {
    display: none;
  }
}
.swiper {
  width: 100%;
  height: 100%;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.small-font {
  font-size: 10px;
}
</style>
