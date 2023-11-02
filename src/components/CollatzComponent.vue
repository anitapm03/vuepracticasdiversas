<template>
    <div>
        <h1>Collatz</h1>

        <label>Inserte un número:</label>
        <input type="nummber" v-model="numero"/>
        <button @click="calcularCollatz()">Calcular!</button>
        <br/>

        <div v-if="numeros.length > 0">
            <ul>
                <li v-for="num in numeros" :key="num" v-html="$filters.evaluarNumero(num)"></li>
            </ul>
        </div>
        
        
    </div>
</template>

<script>
    export default {
        name: "CollatzComponent",
        methods: {
            calcularCollatz(){
                var num = this.numero;
                var aux=[];
                while (num != 1){
                    if (num % 2 == 0){
                        num = num / 2;

                    } else {
                        num = num * 3 + 1;
                    }
                    aux.push(num);
                }
                this.numeros = aux;
            }
        },
        data() {
            return {
                numero: -1,
                numeros: []
            }
        }
    }
</script>