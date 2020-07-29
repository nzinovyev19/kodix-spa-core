<template lang="pug">
  section.contacts
    v-container(v-if="contacts" style="height: 100%")
      BaseTable(
        :data="contacts"
        :headers="tableHeaders"
      )
    v-container(
      v-else
      class="text-center d-flex align-center justify-center"
    )
      v-progress-circular(
        size="100"
        indeterminate
        color="primary"
      )
</template>

<script>
import BaseTable from '@/components/BaseTable.vue';

export default {
  components: {
    BaseTable,
  },
  data() {
    const tableHeaders = {
      name: 'Имя',
      phone_number: 'Номер телефона',
    };
    return {
      contacts: null,
      tableHeaders,
    };
  },
  created() {
    import('@/assets/contacts.json').then((res) => { this.contacts = res.default; });
  },
};
</script>
