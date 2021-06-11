<template>
    <div class="d-flex flex-column align-items-center text-center">
        <img :src="item.poster" :alt="item.poster">
        <h4 class="text-uppercase">{{item.title}}</h4>
        <p><span class="author">{{item.author}}</span><br><span class="year">{{item.year}}</span></p>
    </div>
</template>

<script>
export default {
    name: "SingleAlbum",
    props: ["item"]
}
</script>

<style lang="scss" scoped>
    div {
        height: 380px;
        width: calc(100% / 5 - 20px);
        background-color: #2e3a46;
        margin: calc(25px / 2) 0;

        img {
            width: 80%;
            margin: 20px 0;
        }

        h4 {
            padding: 0 10px;
            font-size: 22px;
            color: white;
            margin-bottom: 10px;
        }

        p {
            color: gray;

            .author {
                font-size: 20px;
            }
            .year {
                font-size: 18px;
            }
        }
    }
</style>