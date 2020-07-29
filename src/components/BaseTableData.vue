<template lang="pug">
  th(v-if="type === 'header'")
    span(
      v-if="withSorting"
      @click="handleClick"
    ) {{ header }} <v-icon small>mdi-swap-vertical</v-icon>
    span(v-else) {{ header }}
  td(v-else) {{ data }}
</template>

<script>
export default {
  props: {
    data: [String, Number],
    type: String,
    headers: Object,
    withSorting: Boolean,
  },
  data() {
    return {
      isAscendingSorting: false,
    };
  },
  computed: {
    header() {
      if (!this.headers) return this.data;
      return this.headers[this.data] || this.data;
    },
  },
  methods: {
    handleClick() {
      if (this.isAscendingSorting) {
        this.$emit('sort', 'descending', this.data);
      } else {
        this.$emit('sort', 'ascending', this.data);
      }
      this.isAscendingSorting = !this.isAscendingSorting;
    },
  },
};
</script>
