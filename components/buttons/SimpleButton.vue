<template>
  <component
    :is="to ? 'n-link' : 'a'"
    :to="to"
    v-bind="$attrs"
    v-on="$listeners"
    >
    <slot />
  </component>
</template>
<script>
export default {
  props: { to: { type: String, default: null } },
};
