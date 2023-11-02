<template>
    <div>
        <h1>Tabla de multiplicar version 1</h1>

        <label>Introduce un número: </label>
        <input type="number" v-model="numero"/>
        <button @click="generarTabla()">Generar tabla</button>

        <!-- METODO Y BOTON -->
        <table border>
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody v-html="html">      
            </tbody>
        </table>

        <br />

        <!-- DIRECTIVAS -->
        <table border>
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody>      
                <tr v-for="num in 10" :key="num">
                    <td>{{numero +"*"+ num}}</td>
                    <td>{{numero * num}}</td>
                </tr>
            </tbody>
        </table>
        <br />

        <!-- CON METODO FILTERS -->

        <table border>
            <thead>
                <tr>
                    <th>Operación</th>
                    <th>Resultado</th>
                </tr>
            </thead>
            <tbody>      
                <tr v-for="num in 10" :key="num">
                    <td>{{$filters.getOperacion(numero,num)}}</td>
                    <td>{{$filters.getMultiplicarNumero(numero,num)}}</td>
                </tr>
            </tbody>
        </table>

    </div>
</template>

<script>
    export default {
        name: "TablaMultiplicar",
        methods: {
            generarTabla(){
                this.html = "";

                for (var i = 0; i < 10; i++){

                    var op = this.numero + " * " + i;
                    var res = this.numero * i;

                    this.html += "<tr>";
                    this.html += "<td>"+op+"</td>";
                    this.html += "<td>"+res+"</td>";
                    this.html += "</tr>";
                }
                
            }
        },
        data() {
            return {
                html: "",
                numero: -1
            }
        }
    }
</script>
