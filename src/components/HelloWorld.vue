<template>
    <div class="container">
        <section class="hero">
            <div class="hero-body">
                <h1 class="title">Welcome!</h1>
                <h2 class="subtitle">Let's try neural networks on a synthetic data</h2>
            </div>
        </section>
        <section class="section">
            <button @click="showScatterPlot" class="button is-info">Show plot</button>
        </section>
    </div>
</template>

<script>
    require('bulma')
    import * as tf from '@tensorflow/tfjs'
    import * as d3 from 'd3'

    const m = 400;
    const N = m / 2;
    const D = 2;

    const X = tf.zeros([m, D]);
    const Y = tf.zeros([m, 1]);
    const a = tf.scalar(4);
    var collect = []

    const z = tf.variable(tf.scalar(32));
    const ranges = tf.range(0,5);
    const randomTf = tf.randomNormal([N]).mul(tf.scalar(0.2))
    var constInit = tf.zeros([m]);

    for (var j=0; j < 3; j++){
        var ix = tf.range(N*j, N*(j+1));
        var t = tf.add(tf.linspace(j*3.12, (j+1)*3.12, N) , randomTf);

        var innermul = tf.mul(t, tf.scalar(4))
        var sinned = tf.sin(innermul)
        var outermul = tf.mul(a, sinned)
        var r = tf.add(outermul , randomTf);
        var costoconcat = tf.mul(r, tf.sin(t));
        var sintoconcat = tf.mul(r, tf.sin(t));
        var last = tf.concat([costoconcat, sintoconcat])


        collect.push(last)


    }


    const stackedX = tf.stack([collect[0], collect[1], collect[2]])

    const oneHalf = tf.fill([200, 1], 0)
    const otherHalf = tf.fill([200, 1], 1);

    const stackedY = tf.concat([oneHalf, otherHalf]);
















export default {
  name: 'HelloWorld',
  data () {
    return {
        message: 'hello'
    }
  },

    mounted() {
        console.log('components was mounted')

    },

    methods: {
        showScatterPlot() {
            const margin = {
                top: 20,
                right: 20,
                bottom: 30,
                left: 40
            };

            const width = 960 - margin.left - margin.right;
            const height = 500 - margin.top - margin.bottom;


            d3.csv('calories.csv').then((error, data) => {
                console.log(error)
            })
        }
    }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
