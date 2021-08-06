<template>
  <p>
    <span><slot name="header"></slot> {{ context ? label + ': ' : label }}</span>
    <span v-if="context" v-text="context"></span>
    <span><slot></slot></span>

  </p>
</template>

<script>
/**
 * 展示什么描述?
 */
export default {
  name: "SomethingShow",
  props: ['label', 'context']
}
</script>
