<template>
    <div class="Conversor">
        <h2>{{moedaA}} para {{moedaB}}</h2>
        <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA" />
        <input type="button" value="Converter" v-on:click="converter" />
        <h2>{{moedaB_value}}</h2>
    </div>
</template>

<script>
    export default{
        name: "Conversor",
        props: ["moedaA", "moedaB"],
        data(){
            return{
                moedaA_value: "",
                moedaB_value: 0
            }
        },
        methods: {
            converter(){
                let de_para = this.moedaA + "_" + this.moedaB;
                let url = "https://free.currconv.com/api/v7/convert?q="+ de_para +"&compact=ultra&apiKey=b220a15a876a5239c30f";

                fetch(url)
                .then(res => {
                    return res.json();
                })
                .then(json => {
                    let cotacao = json[de_para];
                    this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
                });
            }
        }
    };
</script>

<style scoped>

.Conversor{
    background-color: white;
    box-shadow: 2px 2px 10px #333;
    padding: 20px;
    border:none;
    border-radius: 10px;
    max-width: 500px
}

input{
    font-size: 1.2em;
}

input[type="text"]{
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    background-color: #ddd;
    box-shadow: 2px 2px 10px #ddd;
}

input[type="text"]:focus{
    outline: none;
}

input[type="button"]{
    padding: 12px 17px;
    margin-left: 10px;
    border: none;
    box-shadow: 2px 2px 10px #ddd;
    border-radius: 4px;
    background-color: #40476b;
    color: #fff;
}

input[type="button"]:hover{
    cursor: pointer;
    background-color: #fff;
    color: #40476b;
    transition: all .5s;
}

input[type="button"]:focus{
    outline: none;
}

</style>
