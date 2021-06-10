<template>
    <div>
        <img :src="item.poster" :alt="item.poster">
        <h4>{{item.title}}</h4>
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
        height: 350px;
        width: 17%;
        background-color: #2e3a46;
        text-align: center;
        margin: 10px 0;
        display: flex;
        flex-direction: column;
        align-items: center;

        img {
            width: 80%;
            margin: 20px 0;
        }

        h4 {
            padding: 0 10px;
            font-size: 22px;
            color: white;
            text-transform: uppercase;
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