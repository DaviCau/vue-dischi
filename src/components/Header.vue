<template>
    <div class="logo">
        <img src="../assets/img/spotify.png">
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style lang="scss" scoped>
    .logo {
        height: 70px;
        background-color: #2e3a46;
        display: flex;
        align-items: center;

        img {
            height: 50px;
            margin-left: 20px;
        }
    }
</style>