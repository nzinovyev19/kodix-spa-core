<template lang="pug">
  v-simple-table(
    v-if="data.length || headers"
    class="base-table"
    fixed-header
    height="100%"
  )
    template(v-slot:default)
      thead
        tr
          BaseTableData(
            v-for="key in keysOfEntity"
            :key="key"
            type="header"
            :data="key"
            :headers="headers"
            :withSorting="columnsWithSorting && columnsWithSorting.includes(key)"
            @sort="(type, key) => $emit('sort', type, key)"
          )
      tbody(v-if="data.length")
        tr(v-for="item in data" :key="item.id")
          BaseTableData(
            v-for="key in keysOfEntity"
            :key="key"
            :data="item[key]"
          )
      tbody(v-else)
        tr
          BaseTableData(data="Нет данных")
  span(v-else) Данные не загружены
</template>

<script>
import BaseTableData from './BaseTableData.vue';

export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
    headers: {
      type: Object,
    },
    columnsWithSorting: {
      type: Array,
    },
  },
  components: { BaseTableData },
  computed: {
    keysOfEntity() {
      return Object.keys(this.data[0] || this.headers).filter((k) => typeof k !== 'object'); // TODO: MVP
    },
  },
};
</script>

<style lang="sass">
  .base-table
    width: 100%
    height: 100%
    overflow: scroll
</style>
