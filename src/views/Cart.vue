<template>
    <div>
        <div v-for="item in items" :key="item.id">
            <div class="item">
                <div class="image">
                    <img :src="'/images/products/' + item.image">
                </div>
                <div class="info">
                    <h1>{{item.name}}</h1>
                </div>
                <div class="price">
                    <h2>{{item.price}}</h2>
                    <button @click="remove(item)">Remove</button>
                </div>
            </div>
        </div>
        <div>
            <h1>Total: {{cost}}</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Cart',
        data() {
            return {}
        },
        computed: {
            items() {
                return this.$root.$data.cart;
            },
            cost() {
                return '$' + this.$root.$data.cart.reduce((a,i) => a + parseFloat(i.price.slice(1)), 0).toFixed(2)
            }
        },
        methods: {
            remove(item) {
                this.$root.$data.cart = this.$root.$data.cart.filter(i => i.id !== item.id)
            }
        }
    }
</script>
<style scoped>
    .item {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        flex-wrap: nowrap;
        flex-direction: row;
        align-content: space-between;
    }

    .item img {
        height: 60%;
        width: 60%;
    }

    .item .image {
        flex: 0 0 5%;
    }

    .price {
        display: flex;
        justify-content: left;
    }

    .info {
        /*background: #F2921D;*/
        color: #000;
        display: flex;
        justify-content: left;
        flex: 0 0 40%;
        background: #F2921D;
    }

    .price {
        display: flex;
        justify-content: left;
        margin-left: 10px;
    }

    button {
        height: 50px;
        background: #000;
        color: white;
        border: none;
        margin-left: 10px;
    }

    .auto {
        margin-left: auto;
    }
    </style>