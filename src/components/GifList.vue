<template>
  <div id="giflist">
      <gif v-for="gif in gifs" :key="gif.id" :gif="gif"/>
  </div>
</template>

<script>
import Gif from "@/components/Gif";
export default {
    name: "GifList",
    components: {Gif},
    props: {
        gifs: Array
    }
}
</script>

<style>
#giflist{
    margin-bottom: 20px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

}
</style>