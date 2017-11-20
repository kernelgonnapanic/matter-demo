<template>
  <div id="canvas" />
</template>

<script>
import { Engine, Render, World, Bodies } from 'matter-js'
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js PWA'
    }
  },
  mounted () {
    // create an engine
    const engine = Engine.create()

    // create a renderer
    const render = Render.create({
      element: document.getElementById('canvas'),
      engine: engine,
      options: {
        background: '#FFDCE4',
        wireframeBackground: '#FFDCE4'
      }
    })

    // create two boxes and a ground
    const boxA = Bodies.rectangle(400, 200, 80, 80)
    const boxB = Bodies.rectangle(450, 50, 80, 80)
    const ground = Bodies.rectangle(400, 610, 810, 60, { isStatic: true })

    // add all of the bodies to the world
    World.add(engine.world, [boxA, boxB, ground])

    // run the engine
    Engine.run(engine)

    // run the renderer
    Render.run(render)
  }
}
</script>

<style>
#canvas {
  margin: 0 auto;
  width: 800px;
}
</style>

