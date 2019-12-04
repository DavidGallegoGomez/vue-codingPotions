<template>
    <div>
        <p :class="classObject">Primer componente: {{ miVariable }}</p>
        <p v-if="condition">Non Visible</p>
        <p v-show="!condition" :style="styleObject">Show</p>
        <ul>
            <li 
                v-for="(item, i) in miArray" 
                :key="i"
            >
                ID: {{ item.id }} - {{ item.name }} | childrens:
            <span v-for="(children, j) in item.childrens" :key="'child' + j">
                {{ children }}
            </span>
            </li>
        </ul>
        <p>{{ calculateOut() }} - {{ calculateOut() }} - {{ calculateOut() }}</p>
        <!-- <button @click="calculate()">Calculate</button> -->
        <button @click="increment()">Increment</button>
        <span> Current value: {{ miValor }}</span>
        <p> Computed: {{ doble }} - Methods: {{ calculate() }}</p>
    </div>
</template>

<script>
let total = 0;
export default {
    name: "MiComponente",
    data: () => ({
        condition: false,
        miVariable: "Hola mundo",
        miArray: [
            { name: "A", id: 1, childrens: [1, 3, 4] },
            { name: "B", id: 2, childrens: [3, 5, 5] },
            { name: "C", id: 3, childrens: [5, 7, 3] }
        ],
        classObject: {
            active: true,
            "text-danger": false
        },
        styleObject: {
            padding: "10px",
            fontSize: "16px"
        },
        miValor: 20
    }),
    methods: {
        print() {
            this.miVariable = this.miVariable + " No Ejecutable";
        },
        calculate() {
            let aux = this.miValor * 3;
            this.double(aux);
            /* eslint-disable no-console */
            console.log(aux);
            /* eslint-enable no-console */
            return aux;
        },
        double(value) {
            return value * 2;
        },
        calculateOut() {
            // let total = 0;
            total++;
            return total;
        },
        increment() {
            this.miValor++;
        }
    },
    computed: {
        doble() { return this.miValor * 2; }
    }
}
</script>

<style scoped>
    p {
        color: green;
    }
    .active {
        color: black;
    }
    .text-danger {
        color: blueviolet;
    }
</style>