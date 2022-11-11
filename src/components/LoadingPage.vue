<template>
    <div class="page-loader" v-if="!isloaded">
        <b-spinner variant="success" label="Spinning"></b-spinner>
    </div>
</template>
  
<script>
export default {
    name: "PageLoader",
    data: () => {
        return {
            isloaded: false,
        };
    },
    mounted() {
        document.onreadystatechange = () => {
            if (document.readyState == "complete") {
                this.isloaded = true;
            }
        };
    },
};
</script>
  
<style scoped>
.page-loader {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgb(255, 255, 255);
    z-index: 1200;
}
</style>
  