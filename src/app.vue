

<template>
    <div id="app">
        <h1>Monty Hall Problem</h1>
        <div class="form">
            <div v-if="!started">
                <label for="doorsAmount">How many doors?</label>
                <input type="text" id="doorsAmount" size="3" v-model.number="doorsAmount">
            </div>
            <div v-if="!started">
                <label for="selectedDoor">Award winning door?</label>
                <input type="text" id="selectedDoor" size="3" v-model.number="selectedDoor">
            </div>
            <button v-if="!started" @click="started = true"> Start </button>
            <button v-if="started" @click="started = false"> Restart </button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="i in doorsAmount" :key="i">
                <door :hasGift="i === selectedDoor" :number="i" />
            </div>
        </div>
    </div>
</template>

<script>
    import door from './components/door';
    
    export default {
        name: 'App',
        components: {
            door
        },
        data() {
            return {
                started: false,
                doorsAmount: 3,
                selectedDoor: null
            }
        }
    }
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
body {
  color: #fff;
  background: linear-gradient(to right, rgb(21, 153, 87), rgb(21, 87, 153));
  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
    .form {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      margin-bottom: 40px;
      margin-bottom: 10px;
      font-size: 2rem;
      input {
        margin-bottom: 10px;
        font-size: 2rem;
      }
      button {
        margin-bottom: 10px;
        font-size: 2rem;
      }
    }
    & h1 {
        border: 1px solid #000;
        background-color: #0004;
        padding: 20px;
        margin-bottom: 60px;
    }
    .doors {
        align-self: stretch;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
    }
  }
}
</style>
