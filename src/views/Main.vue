<template>
    <div>
        <input type="text" v-model="number" placeholder="Input Angka">
        <br>
        <button @click="generateSegitiga(this.number)">Generate Segitiga</button>
        <button @click="generateGanjil(this.number)">Generate Bilangan Ganjil</button>
        <button @click="generatePrima(this.number)">Generate Bilangan Prima</button>
        <br>
        <h1>Result:</h1>
        <div :key="key" v-for="(value, key) in result">
            {{value}}
        </div>
        <br>
    </div>
</template>

<script>
    export default {
        data: function() {
            return {
                number: 0,
                baseUrl: "http://localhost:3000",
                result: []
            }
        },
        methods: {
            generateSegitiga(number) {
                if (number <= 0) {
                    alert("Please enter number greater than 0")
                    return
                }
                this.axios.post(this.baseUrl+"/segitiga", {input: number.toString()})
                    .then((response) => {
                        this.result = response.data
                    })
                return
            },
            generateGanjil(number) {
                if (number <= 0) {
                    alert("Please enter number greater than 0")
                    return
                }
                this.axios.post(this.baseUrl+"/ganjil", {input: number.toString()})
                    .then((response) => {
                        this.result = [response.data.join(" ")]
                    })
                return
            },
            generatePrima(number) {
                if (number <= 0) {
                    alert("Please enter number greater than 0")
                    return
                }
                this.axios.post(this.baseUrl+"/prima", {input: number.toString()})
                    .then((response) => {
                        this.result = [response.data.join(" ")]
                    })
                return
            },
        }
    }
</script>