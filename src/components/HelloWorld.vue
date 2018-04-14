<template>
    <div class="hello">
        <h1>{{ message }}</h1>
    </div>
</template>

<script>
    import * as tf from '@tensorflow/tfjs'

    const m = 400;
    const N = m / 2;
    const D = 2;

    const X = tf.zeros([m, D]);
    const Y = tf.zeros([m, 1]);
    const a = tf.scalar(4);

    const z = tf.variable(tf.scalar(32));
    const ranges = tf.range(0,5);
    const randomTf = tf.randomNormal([N]).mul(tf.scalar(0.2))

    for (var j=0; j < 3; j++){
        var ix = tf.range(N*j, N*(j+1));
        var t = tf.add(tf.linspace(j*3.12, (j+1)*3.12, N) , randomTf);

        var innermul = tf.mul(t, tf.scalar(4))
        var sinned = tf.sin(innermul)

        var outermul = tf.mul(a, sinned)

        var r = tf.add(outermul , randomTf);

        var costoconcat = tf.mul(r, tf.sin(t))
        costoconcat.print()


        // X[ix] = tf.concat([r * Math.sin(t), r * Math.cos(t)])
        // var last = tf.mul(r, tf.sin(t)).concat(tf.mul(r, tf.cos(t)))
        // console.log(last)
        // var sined = r.mul(tf.scalar(Math.sin(t)));
        // var cossed = r.mul(tf.scalar(Math.cos(2)))



    }





    // const zind = tf.variable(tf.zeros([3,2]));
    // const zindi = tf.zeros([3,2]);
    // console.log(zindi.add(tf.zeros([3,2])).print());

  const x = tf.tensor1d([1,2,3,4])
  const indices = tf.tensor1d([1,3,3]);




export default {
  name: 'HelloWorld',
  data () {
    return {
        message: 'hello'
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
