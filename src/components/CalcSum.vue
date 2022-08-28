<template>
  <div class="calc">
    <div class="calc__screen">
      <input type="number" v-model.number="op1">
      <input type="number" v-model.number="op2">
      = {{ sum }}
    </div>
    <div class="keyboard">
      <div class="keyboard__operations">
        <button v-for="operation in operations" :key="operation" @click="count(operation)">
          {{ operation }}
        </button>
      </div>
      <div class="keyboard__keys">
        <div class="checkbox">
          <input type="checkbox" id="checkbox" v-model="checked">Отобразить экранную клавиатуру
        </div>
        <label for="checkbox" class="keyboard__screen" v-if="checked">
          <button v-for="btn in keyboard" :key="btn" @click="input(btn, picked)">{{ btn }}</button>
        </label>
        <div class="keyboard__radio">
          <input type="radio" name="radio" id="one" v-on:change="leverOp1 ()" checked>
          <label for="one">1ый операнд</label>
          <input type="radio" name="radio" id="two" v-on:change="leverOp2 ()">
          <label for="two">2ый операнд</label>
          <!--          <input type="radio" name="radio"  v-model="picked" :checked="checked">-->
          <!--          <label for="one">Один</label>-->
          <!--          <input type="radio" name="radio" v-model="picked">-->
          <!--          <label for="two">Два</label>-->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcSum',
  data: () => ({
    sum: 0,
    op1: 0,
    op2: 0,
    operations: ['+', '-', '*', '/', '//', '^'],
    keyboard: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 'Backspace'],
    checked: true,
    picked: true

  }),
  methods: {
    count (operation) {
      const {
        op1,
        op2
      } = this
      switch (operation) {
        case '+':
          this.sum = op1 + op2
          break
        case '-':
          this.sum = op1 - op2
          break
        case '*':
          this.sum = op1 * op2
          break
        case '/':
          this.sum = op1 / op2
          break
        case '^':
          this.sum = Math.pow(op1, op2)
          break
        case '//':
          this.sum = Math.floor(op1 / op2)
          break
      }
    },
    input (btn, pick) {
      let op
      pick === true ? op = this.op1 : op = this.op2

      if (btn === 'Backspace' && op !== '') {
        const arr = +(op.toString().split('').slice(0, -1).join(''))
        op = arr
      } else if (op > 0) {
        op = +(op.toString() + btn)
      } else {
        op = btn
      }
      pick === true ? this.op1 = op : this.op2 = op
    },
    leverOp1 () {
      this.picked = true
    },
    leverOp2 () {
      this.picked = false
    }
  }
}
</script>

<style scoped lang="scss">
.calc__screen {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

.keyboard {
  display: flex;
  justify-content: center;
  flex-direction: column;
  gap: 20px;

  &__screen {
    @extend .keyboard;
    flex-direction: row;
    gap: 5px;
  }

  &__keys {
    @extend .keyboard;
  }
}

</style>
