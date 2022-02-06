<template>
  <div class="gif" :style="`background-image: url(${gif.images.original.url})`" style="flex: 1">
      <input ref="url" readonly type="text" :value="gif.images.original.url">
      <button @click="copyUrl">Copy</button>
  </div>
</template>

<script>
export default {
    name: "Gif",
    props: {
        gif: Object
    },
    methods: {
        copyUrl() {
            this.refs.url.select();
            document.execCommand('copy');
            this.refs.url.value='Copied!!!!'
        }
    }
}
</script>

<style>
.gif{
    margin-bottom: 20px;
    width: 240px;
    height: 240px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
}
</style>