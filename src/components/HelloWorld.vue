<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
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

    for (var j=0; j < 3; j++){
        var ix = tf.range(N*j, N*(j+1));
        var t = tf.add(tf.linspace(j*3.12, (j+1)*3.12, N) , tf.randomNormal([N]).mul(tf.scalar(0.2)));

        var r = a.mul(tf.scalar(Math.sin(tf.scalar(4).mul(t)))) + tf.randomNormal([N]).mul(tf.scalar(2));

        // X[ix] = tf.concat([r * Math.sin(t), r * Math.cos(t)])
        // var sined = r.mul(tf.scalar(Math.sin(t)));
        // var cossed = r.mul(tf.scalar(Math.cos(2)))
        console.log(tf.mul(r, tf.scalar(2.3)));



    }


    // const zind = tf.variable(tf.zeros([3,2]));
    // const zindi = tf.zeros([3,2]);
    // console.log(zindi.add(tf.zeros([3,2])).print());






    export default {
        name: 'HelloWorld',
        data() {
            return {
                msg: 'Welcome to Your Vue.js App',
            }
        },

        methods: {}
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
