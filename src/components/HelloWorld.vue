<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <portal-target
      slim
      name="with-custom-transition"
      :transition="customPortalTransition"
    />
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  computed: {
    // not even commenting out will make the test pass
    // it needs to be removed completely from the source code
    customPortalTransition() {
      return {
        functional: true,
        render (h, context) {
          return h('transition', { props: { name: 'with-custom-transition' } }, context.children)
        }
      }
    }
  }
}
</script>