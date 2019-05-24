<template>
  <h1>Hello world !</h1>
</template>


<script>
const math = require('mathjs')

export default {
  created() {
    this.case1();
  },
  methods: {
    case1() {
      const node2 = math.parse('foo + bar')
      const code2 = node2.compile()

      var scope = {
        foo: 56,
        bar: 62,
      };
      console.log("customs.js object.constructor === Object")
      console.log(scope.constructor === Object);
      /* Debug
      console.log(scope.constructor);
      console.log(scope.constructor.toString());
      console.log(Object.constructor);
      console.log(Object.constructor.toString());
      console.dir(scope,{depth:null})
      const util = require('util');
      console.log(util.inspect(scope, {showHidden: true, depth: null}))
      */
      return code2.eval(scope);
    },
    case2() {
      return math.eval('foo + bar', {
        foo: 56,
        bar: 62,
      });
    },
  }
}
</script>
