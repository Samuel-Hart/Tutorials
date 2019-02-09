<template>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div class="btn operator">X</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div class="btn operator">+</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div class="btn operator">-</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot()" class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            current: '52',
            operand: 0,
        }
    },
    methods: {
        clear() {
            this.current = '';
        },
        sign() {
            this.current = `${parseFloat(this.current) * -1}`;
        },
        percent() {
            this.current = `${parseFloat(this.current)/100.0}`;
        },
        append(number) {
            this.current = `${this.current}${number}`;

        },
        dot(){
            if (this.current === '')
            {
                this.current = '0';
            }

            if(this.current.indexOf('.')===-1){
                this.append('.');
            }
        }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.btn{
    background-color: #eee;
    border: 1px solid #999;
}

.calculator {
    width: 400px;
    margin: 0 auto;
    font-size:40px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
}

.display {
    grid-column: 1/5;
    background-color: black;
    color: #eee;
}

.zero {
    grid-column:1/3;
}

.operator {
    background-color:orange;
    color: #eee;
}

</style>
