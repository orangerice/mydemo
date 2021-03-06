<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App222212',
        arr: [{
          name: 'james',
          age: 21
        }, {
          name: 'wade',
          age: 22
        }]
      }
    },
    methods: {
      init1() {
        return new Promise((resolve, reject) => {
          this.arr.forEach((item, index) => {
            item['club'] = 'heat'
          })
          resolve(this.arr)
        })
      },
      init2() {
        return new Promise((resolve, reject) => {
          this.init1().then(res => {
            res.forEach((item, index) => {
              if (item.age > 21) {
                item['limit'] = true
              }
            })
            resolve(res)
          },err=>{

          })
        })
      },
      init3(){
        this.init2().then(res=>{
          console.log('333333',res)
        })
      }
    },
    mounted() {
      // test
      this.init3()
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>
