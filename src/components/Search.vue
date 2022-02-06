<template>
    <input placeholder="Type something to search for awesome gif" v-model="keyword" @input="onInput">
</template>

<script>

export default {
    name: "Search",
    data(){
        return{
            keyword: '',
            timeout:null,
        }
    },
    methods: {
        onInput(){
            clearTimeout(this.timeout);
            this.timeout = setTimeout(() => {
                this.search();
            }, 500)
        },
        search(){
            fetch(`http://api.giphy.com/v1/gifs/search?api_key=UQuhL3i0Xzhy5b9f7JyszfTXCrNzoE8C&q=${this.keyword}&limit=9`)
            .then(response => response.json())
            .then(result => {
                console.log(result);
                this.$emit('fetch-gifs', result.data);
            })
        }
    }
}
</script>

<style scoped>
input{
    padding: 10px 16px;
    border-radius: 4px;
    font-size: 18px;
    outline:0;
    border: 2px solid #5f5f5f;
    display: block;
    width: 100%;
}
input:focus{
    border-color: #0539e4;
}

</style>