<template>
    <div id="app">
        <div class="linha">
            <Conversor moeda-a="USD" moeda-b="BRL"/>
            <Conversor moeda-a="BRL" moeda-b="USD"/>
        </div>

        <div class="linha">
            <Conversor moeda-a="CAD" moeda-b="BRL"/>
            <Conversor moeda-a="BRL" moeda-b="CAD"/>
        </div>

        <div class="linha">
            <Conversor moeda-a="EUR" moeda-b="BRL"/>
            <Conversor moeda-a="BRL" moeda-b="EUR"/>
        </div>

    </div>
</template>

<script>
import Conversor from './components/Conversor.vue'

export default {
  name: 'app',
  components: {
    Conversor
  }
}
</script>

<style>
body{
    background-color: #1a192e;
}

#app{
    font-family: 'Poppins';
    text-align: center;
    max-width: 900px;
    margin: auto;
}

.linha{
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
}
</style>
