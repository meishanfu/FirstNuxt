<template>
<div>
    <b-card v-bind:title="title" v-bind:img-src="imgsrc" img-alt="Image" img-top tag="article" style="max-width: 20rem;" class="mb-2">
        <b-card-text>
            {{text}}
        </b-card-text>
        <div class="row">
            <b-button v-on:click="sub()" variant="light">-</b-button>
            <span>
                <strong> {{ count }}</strong>
            </span>
            <b-button v-on:click="add()" variant="light">＋</b-button>
        </div>
        <br>        
        <b-button variant="outline-primary" @click="addCart">加入購物車</b-button>
    </b-card>
</div>
</template>

<script>
export default {
    props: ["id", "text", "imgsrc", "title"],
    data: function () {
        return {
            count: 1,
            msg: ""
        }
    },
    methods: {
        add: function () {
            if (this.count < 10) {
                this.count = this.count + 1;
            }
        },
        sub: function () {
            if (this.count > 1) {
                this.count = this.count - 1;
            } else {
                this.count = 1
            }
        },
        addCart(){
            this.$store.commit('addCart',{id:this.id,count:this.count})

        }
        
    }
}
</script>

<style>
</style>
