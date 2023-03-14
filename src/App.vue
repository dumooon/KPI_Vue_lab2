<template>
  <div class="container">
    <div class="card center">
    <header>
      <h2 >Лабораторна робота №2</h2>
      <h3>Варіант № 17</h3>
      <p>Виконав студент групи ТР-24 Ніколаєнко Дмитро</p>
    </header>
    <hr>
    <main>
     <div class="container">
      <h3>Умова:</h3>
      <p>Розробити програми згідно з алгоритмом з використанням рекурсивної функції та без використання рекурсивної функції (ітераційним методом). Оцінити час виконання та складність алгоритму.</p>
      <h3>Завдання №1</h3>
      <p>ітераційний метод</p>
      <button @click="task1" class="btn primary" >Виконати</button>
      <hr />
      <h3>Завдання №2</h3>
      <p>Рекурсивний метод</p>
      <button @click="task2" class="btn primary" >Виконати</button>
      <hr />
      <div class="form-control">
        <input 
          v-model="n"  
          type="text" 
        >
      </div>
      <div v-if="flag1">
        <h3>Результат ітераційного алгоритму: р = {{pIter}}</h3>
        <h4>К-ть ітерацій: {{this.iteration1}}</h4>
        <h4>Час виконання: {{this.time1}} наносекунд</h4>
      </div>
      <div v-if="flag2">
        <h3>Результат рекурсивного алгоритму: p = {{pRec}}</h3>
        <h4>К-ть ітерацій: {{this.iteration2}} </h4>
        <h4>Час виконання: {{this.time2}} наносекунд</h4>
      </div>
    
     </div> 
    </main>
    </div>
  </div>
</template>

<script>


export default {
  
  data() {
    return{
      n: '',
      flag1: false,
      flag2: false,
      pIter: 1,
      pRec: 0,
      recCounter: 0,
      iteration1: 0,
      iteration2: 0,
      time1: 0,
      time2: 0
      
    }
  },
  methods: {
    task1() {
      const start = performance.now()

      for (let i = 0; i < this.n; i++){
        this.iteration1++
        let x = i + 1
        let iterationRez = Math.sin(x)/(Math.pow(x, 2) + 1)
        this.pIter *= iterationRez
      }
      const end = performance.now();
     
      this.time1 = (end - start) * 1000000;
      this.flag1 = true
    },
    //---------------------------------------------------------------------
    task2() {
      const start = performance.now()
      this.pRec = this.pRecRecursive(this.n);
      this.flag2 = true
      const end = performance.now();
      this.time2 =  (end - start) * 1000000;
    },
    pRecRecursive(n) {
      this.iteration2++
      // базовий випадок - якщо n == 0, повернути 1
      if (n === 0) {
      return 1;
      }
      // інакше обчислити значення ітерації
      let x = n;
      let iterationRez = Math.sin(x) / (Math.pow(x, 2) + 1);
      // викликати рекурсивно зменшення розміру задачі
      return iterationRez * this.pRecRecursive(n - 1);
    }
  }
}
</script>

<style>

</style>
