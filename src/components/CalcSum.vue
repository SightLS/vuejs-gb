<template>
  <div class="calc">
    <div class="calc__screen">
      <input type="number" v-model.number="op1">
      <input type="number" v-model.number="op2">
      = {{ sum }}
    </div>
    <div class="keyboard">
      <button v-for="operation in operations" :key="operation" @click="count2(operation)">
        {{ operation }}
      </button>
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
    operations: ['+', '-', '*', '/', '//', '^']
  }),
  methods: {
    count2 (operation) {
      switch (operation) {
        case '+':
          this.sum = this.op1 + this.op2
          break
        case '-':
          this.sum = this.op1 - this.op2
          break
        case '*':
          this.sum = this.op1 * this.op2
          break
        case '/':
          this.sum = this.op1 / this.op2
          break
        case '^':
          this.sum = Math.pow(this.op1, this.op2)
          break
        case '//':
          this.sum = Math.floor(this.op1 / this.op2)
          break
      }
    }
  }
}
</script>

<style scoped>
.calc__screen {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

</style>
