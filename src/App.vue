<template>
    <div id="app">
        <div class="container">
            <div
                v-for="(row, ri) in values"
                :key="ri"
                class="row">
                <div
                    v-for="(col, ci) in row"
                    :key="ci"
                    v-on:click= "addSymbol (ri,ci)"
                    class="col">
                    {{col}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from 'vue'

export default {
    name: 'app',
    data() {
        return {
            isPlayer :true,
            nbCase:3,
            values: []
        }
    },

    methods :{
        addSymbol(row, col) {
            Vue.set(this.values [row], col, this.isPlayer ? 'X' : 'O')
            this.isPlayer = !this.isPlayer
        },
    },

    created () {
        for (let i = 0; i < 3; i++){
            const row = []
            this.values.push(row)
            for (let j = 0; j < 3; j++){
                row.push(null)
            }
        }
    }
}

</script>


<style>
body {
    margin: 0;
    background-color:black ;
}

#app {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 100vw;

}
.container {
    display: flex;
    flex-direction: column;
    width: 600px;
    height: 600px;
}

.row {
    display: flex;
    flex: 0 33.33%;
    border-width: medium;
    border-color: rgb(186, 231, 24);
}

.col {
    flex: 0 33.33%;
    height: 100%;
    border: 1px solid;
    background-color: rgb(186, 231, 24);
    font-size: 8rem;
    text-align: center;
}


</style>
