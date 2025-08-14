<script setup>
import { defineProps, defineEmits } from "vue";
const props = defineProps({
  favList: {
    type: Array,
    default: () => [],
  },
});
const emit = defineEmits(["remove-fav"]);
const removeFav = (item) => emit("remove-fav", item);
</script>

<template>
  <div class="favList">
    <div v-if="!favList.length" class="nodata">還沒有加入收藏喔</div>
    <div class="container" v-else>
      <div class="list" v-for="item in favList" :key="item.id">
        <img :src="item.images" />
        <div class="list_content">
          <h6>{{ item.name }}</h6>
          <p>{{ item.artists }}</p>
        </div>
        <div class="list_action">
          <button @click="removeFav(item)">X</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.favList {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 0.5rem;
  .nodata {
    width: 100%;
    height: 10rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .container {
    overflow: hidden;
    padding: 5rem 0.5rem 0.5rem 0.5rem;
  }
  .list {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.5rem;
    img {
      width: 4rem;
    }
    &_content {
      flex: 0 1 calc(100% - 7.5rem);
      h6 {
        font-size: 0.8rem;
      }
      p {
        font-size: 0.75rem;
      }
    }
    &_action {
      display: flex;
      flex-direction: row;
      align-items: center;
      width: 2.5rem;
      button {
        background-color: transparent;
        color: rgb(175, 50, 119);
      }
    }
  }
}
</style>
