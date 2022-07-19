<template>

    <div class="card">
        <img src="../assets/christopher-campbell-rDEOVtE7vOs-unsplash.jpg" alt="Profile-Picture" style="width:100%">
        <h1>{{ name }}</h1>
        <p class="title">
        <div v-for="pro in profession">{{ pro }}</div>
        </p>
        <div v-if="favourite">
            <p class="favorite-heart"><i class="fa fa-heart" aria-hidden="true"></i></p>
        </div>
        <div v-else>
            <p class="non-favorite-heart"><i class="fa fa-heart" aria-hidden="true"></i></p>
        </div>
        <p><button v-on:click="toggleFavorites">Favorite</button></p>
    </div>
</template>

<script>
export default {
    name: "User Profile",
    props: {
        name: {
            type: String,
            required: true
        },
        profession: {
            type: Object,
            required: true
        },
        image_url: {
            type: String,
            required: false
        },
        favourite: {
            type: Boolean,
            required: false
        }
    },
    methods: {
        toggleFavorites() {
            this.favorite ? this.favorite = false : this.favorite = true
            this.$emit('favorite', this.favorite)
        }
    }
}

</script>


<style>
.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    max-width: 300px;
    margin: auto;
    text-align: center;
    font-family: arial;
}

.title {
    color: grey;
    font-size: 18px;
}

button {
    border: none;
    outline: 0;
    display: inline-block;
    padding: 8px;
    color: white;
    background-color: #000;
    text-align: center;
    cursor: pointer;
    width: 100%;
    font-size: 18px;
}

a {
    text-decoration: none;
    font-size: 22px;
    color: black;
}

button:hover,
a:hover {
    opacity: 0.7;
}

.favorite-heart {
    color: red;
}

.non-favorite-heart {
    color: black;
}
</style>