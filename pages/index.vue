<template>
<div>
  <h1>Hello world !</h1>

  {{ case1() }}
  <!--
    {{ case2() }}
  -->

  <!--
    {{ !$isServer && case1() }}
    {{ !$isServer && case2() }}
  -->
  </div>
</template>

<script>
const math = require('mathjs')

export default {
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
