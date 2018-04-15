<template>
  <div class="hello">
    <h2>{{ shape }}</h2>
  </div>
</template>

<script>

  import * as tf from '@tensorflow/tfjs'

  const m = 400;
  const N = m/2;
  const D = 2;

  var X = tf.zeros([m,D]);
  const Y = tf.zeros([m, 1]);
  var collect = [];

  const a = 4;

  const r = tf.range(0,4)

  for (var j=0; j < 2; j++) {

      const ix = tf.range(N*j, N*(j+1))
      const t = tf.add(tf.linspace(j*3.12,(j+1)*3.12,N) , tf.randomNormal([N]).mul(tf.scalar(0.2)))
      const r = tf.add(tf.sin(tf.scalar(4).mul(t)) , tf.randomNormal([N]).mul(tf.scalar(0.2)));
      const last = tf.mul(r, tf.sin(t)).concat(tf.mul(r, tf.cos(t)))
      collect.push(last)


  }

  console.log(collect)
  const stacked = tf.stack([collect[0], collect[1]]);
  stacked.print()

  const Ycreated = tf.fill([1, 200], 0).concat(tf.fill([1, 200], 1))


  const x = tf.tensor1d([1,2,3,4])
  const range = tf.range(1,3);
  // x[range].print()
  tf.gather(x, range)






export default {
  name: 'HelloWorld',
  data () {
    return {
        message: 'hello',
        shape: Ycreated.shape
    }
  },

    mounted() {
        console.log('components was mounted')

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
