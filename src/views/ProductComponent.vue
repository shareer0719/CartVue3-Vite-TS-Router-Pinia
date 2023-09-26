<script setup lang="ts">
import { ref } from "vue";
import { ElRow, ElCol, ElCard, ElButton } from "element-plus";
import { useProductStore } from "@/stores/counter.ts"; //引入stores
const productStore = useProductStore(); //使用
</script>

<template>
  <h2 class="intro" style="text-align: center">商品列表</h2>
  <el-row style="margin: 20px; display: flex; justify-content: center">
    <el-col
      v-for="(i, index) in productStore.products"
      :id="index"
      :key="index"
      :span="5"
      style="margin: 10px"
    >
      <el-card :body-style="{ padding: '0px' }" shadow="hover">
        <img :src="i.image" class="image" />
        <div style="padding: 14px">
          <span>{{ i.title }}</span>
          <div class="bottom">
            <p class="time">$ {{ i.price }}</p>
            <el-button @click="productStore.addIntoCart(i)" class="button"
              >加入購物車</el-button
            >
          </div>
        </div>
      </el-card>
    </el-col>
  </el-row>
</template>
<style>
.time {
  font-size: 12px;
  color: #999;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.button {
  padding: 10px;
  min-height: auto;
  background-color: lightYellow;
  color: black;
  border-radius: 8px;
}

.button:active {
  padding: 5px;
  min-height: auto;
  background-color: black;
  color: white;
}

.button:hover {
  background-color: white;
  color: black;
  border: 2px solid lightblue;
}

.image {
  width: 100%;
  display: block;
}
</style>