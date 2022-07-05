<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>
        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">Quantas portas?</label>
                <input
                    type="text"
                    id="portsAmount"
                    size="3"
                    v-model.number="portsAmount"
                />
            </div>
            <div v-if="!started">
                <label for="selectedPort">Qual porta é premiada?</label>
                <input
                    type="text"
                    id="selectedPort"
                    size="3"
                    v-model.number="selectedPort"
                />
            </div>
            <button
                v-if="!started"
                @click="started = true"
                class="custom-btn btn"
            >
                Iniciar
            </button>
            <button
                v-if="started"
                @click="started = false"
                class="custom-btn btn"
            >
                Reiniciar
            </button>
        </div>
    </div>
    <div class="doors" v-if="started">
        <div v-for="i in portsAmount" :key="i">
            <Door :hasGift="i === selectedPort" :number="i" />
        </div>
    </div>
</template>

<script>
import Door from "./components/Door.vue";
export default {
    components: { Door },
    name: "App",
    data: function () {
        return {
            started: false,
            portsAmount: 3,
        };
    },
};
</script>

<style>
:root {
    --primary-light: #8abdff;
    --primary: #6d5dfc;
    --primary-dark: #5b0eeb;

    --white: #ffffff;
    --greyLight-1: #e4ebf5;
    --greyLight-2: #c8d0e7;
    --greyLight-3: #bec8e4;
    --greyDark: #9baacf;
}

* {
    box-sizing: border-box;
    font-family: "Montserrat", sans-serif;
}
body {
    color: #fff;
    background-color: var(--primary);
}
#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}

#app h1 {
    border-bottom: 2px solid #fff;
    padding: 20px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form,
.form input,
.form button {
    margin-bottom: 10px;
    font-size: 2rem;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

input{
    color: #fff;
    margin-left: 15px;
    padding:10px;
    border:none;
    border-bottom:1px solid #fff;
    background-color: transparent;
}


.custom-btn {
    color: #fff;
    border-radius: 5px;
    padding: 10px 25px;
    font-weight: 500;
    background: transparent;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: inset 2px 2px 2px 0px rgba(255, 255, 255, 0.5),
        7px 7px 20px 0px rgba(0, 0, 0, 0.1), 4px 4px 5px 0px rgba(0, 0, 0, 0.1);
    outline: none;
}

.btn {
    background-color: #c797eb;
    line-height: 42px;
    border: none;
}
.btn:hover {
    background: transparent;
}
.btn span:hover {
    color: #c797eb;
}
</style>
