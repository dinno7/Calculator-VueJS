<template>
    <div class="container">
        <div class="calc mx-auto">
            <div class="up">
                <input type="text" v-model="currentNum">
            </div>
                <div class="keys w-100">
                    <div class="row">
                        <div class="col">
                            <button class="btn btn-warning" @click="plusMinusNumber">+/-</button>
                            <button class="btn btn-warning" @click="operationHandle('%')">%</button>
                            <button class="btn btn-warning" @click="operationHandle('/')">/</button>
                            <button class="btn btn-danger" @click="backSpace">
                               <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-backspace" viewBox="0 0 16 16">
                                    <path d="M5.83 5.146a.5.5 0 0 0 0 .708L7.975 8l-2.147 2.146a.5.5 0 0 0 .707.708l2.147-2.147 2.146 2.147a.5.5 0 0 0 .707-.708L9.39 8l2.146-2.146a.5.5 0 0 0-.707-.708L8.683 7.293 6.536 5.146a.5.5 0 0 0-.707 0z"/>
                                    <path d="M13.683 1a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2h-7.08a2 2 0 0 1-1.519-.698L.241 8.65a1 1 0 0 1 0-1.302L5.084 1.7A2 2 0 0 1 6.603 1h7.08zm-7.08 1a1 1 0 0 0-.76.35L1 8l4.844 5.65a1 1 0 0 0 .759.35h7.08a1 1 0 0 0 1-1V3a1 1 0 0 0-1-1h-7.08z"/>
                                </svg>
                            </button>
                        </div>
                        <div class="col">
                            <button class="btn btn-light" @click="addNumber('7')">7</button>
                            <button class="btn btn-light" @click="addNumber('8')">8</button>
                            <button class="btn btn-light" @click="addNumber('9')">9</button>
                            <button class="btn btn-warning" @click="operationHandle('*')">x</button>
                        </div>
                        <div class="col">
                            <button class="btn btn-light" @click="addNumber('4')">4</button>
                            <button class="btn btn-light" @click="addNumber('5')">5</button>
                            <button class="btn btn-light" @click="addNumber('6')">6</button>
                            <button class="btn btn-warning" @click="operationHandle('-')">-</button>
                        </div>
                        <div class="col">
                            <button class="btn btn-light" @click="addNumber('1')">1</button>
                            <button class="btn btn-light" @click="addNumber('2')">2</button>
                            <button class="btn btn-light" @click="addNumber('3')">3</button>
                            <button class="btn btn-warning" @click="operationHandle('+')">+</button>
                        </div>
                        <div class="col">
                            <button class="btn btn-danger" @click="clear">C</button>
                            <button class="btn btn-light" @click="addNumber('0')">0</button>
                            <button class="btn btn-light" @click="addDot">.</button>
                            <button class="btn btn-success" @click="equal">=</button>
                        </div>
                    </div>
                </div>
        </div>
    </div>    
</template>


<script>
    export default {
        name: 'Calculator',
        data(){
            return{
                currentNum:'0',
                savedNum:'',
                operation:''
            }
        },
        methods: {
            addNumber(number){
                if(this.currentNum == 0) this.currentNum = '';
                else if(this.currentNum == 0 && number == 0) return; 
                this.currentNum += number;
            },
            addDot(){
                if(!this.currentNum.includes('.')){
                    this.currentNum += '.'
                }
            },
            plusMinusNumber(){
                if(this.currentNum > 0){
                    this.currentNum = '-' + this.currentNum;
                }
                else if(this.currentNum < 0){
                    this.currentNum = this.currentNum.slice(1)
                }
            },
            operationHandle(operation){
                
                this.savedNum = this.currentNum;
                this.currentNum = '';
                this.operation = operation;
            },
            equal(){
                switch(this.operation){
                    case '+':
                        this.currentNum = String(parseFloat(this.savedNum) + parseFloat(this.currentNum))
                        break;
                    case '-':
                        this.currentNum = String(parseFloat(this.savedNum) - parseFloat(this.currentNum))
                        break;
                    case '*':
                        this.currentNum = String(parseFloat(this.savedNum) * parseFloat(this.currentNum))
                        break;
                    case '/':
                        this.currentNum = String(parseFloat(this.savedNum) / parseFloat(this.currentNum))
                        break;
                    case '%':
                        this.currentNum = String(parseFloat(this.savedNum) % parseFloat(this.currentNum))
                        break;
                }
            },
            backSpace(){
                if(this.currentNum.length > 1){
                  this.currentNum =  this.currentNum.slice(0 ,this.currentNum.length - 1)
                }
                else if(this.currentNum.length > 0) this.currentNum = '0'
            },
            clear(){
                this.currentNum = '0'
            },
        },
    }
</script>


<style>
.calc{
    width:300px;
}
.calc .up {
    display: flex;
    border-radius: 10px;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;
    align-items: center;
    min-height: 100px;
    background-color: #262626;
}
.calc .up input{
    width: 100%;
    padding-left: 30px;
    line-height: 30px;
    font-size: 30px;
    background-color: transparent;
    color: white;
    outline: none;
    border: none;
}
.calc .keys{
    width: 100%;
    border-radius: 10px;
    border-top-left-radius: 0;
    border-top-right-radius: 0;
    padding-top: 40px;
    padding-left: 15px;
    min-height: 380px;
    background-color: #424242;
}
.calc .keys button{
    font-size: 19px;
    width: 50px;
    height: 50px;
    margin: 0 15px 15px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    
}
.col{
    display: flex;
    justify-content: center;
    align-content: center;
}
</style>
