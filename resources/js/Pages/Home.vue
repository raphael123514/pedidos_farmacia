<template>
  <div class="p-6">
    <div class="pl-6 pb-3">
      <ButtonAdd :action="teste" />
      
    </div>
    <Body>
      <TableComponent :columns="columns" :rows="rows" />
      
    </Body>

  </div>

</template>

<script>
import TableComponent from '@/Components/TableComponent.vue'
import ButtonAdd from '@/Components/ButtonAdd.vue'
import Body from '@/Components/Body.vue'

export default {
  components: {
    TableComponent,
    Body,
    ButtonAdd
  },
  data() {
    return {
      columns: [
        { key: 'id', label: 'ID' },
        { key: 'responsavel', label: 'Responsável' },
        { key: 'cliente', label: 'Cliente' },
        { key: 'data_pedido', label: 'Data/hora do pedido' },
        { key: 'data_entrega', label: 'Data/hora da entrega' },
        { key: 'data_vencimento', label: 'Data/hora do vencimento' },
        { key: 'acoes', label: '' }
      ],
      rows: [
        { "id": 1, "responsavel": "João Silva", "cliente": "Farmácia A", "data_pedido": "2023-10-01 10:00", "data_entrega": "2023-10-05 14:00", "data_vencimento": "2023-11-01 10:00" },
        { "id": 2, "responsavel": "Maria Oliveira", "cliente": "Farmácia B", "data_pedido": "2023-10-02 11:00", "data_entrega": "2023-10-06 15:00", "data_vencimento": "2023-11-02 11:00" },
        { "id": 3, "responsavel": "Carlos Souza", "cliente": "Farmácia C", "data_pedido": "2023-10-03 12:00", "data_entrega": "2023-10-07 16:00", "data_vencimento": "2023-11-03 12:00" },
        { "id": 4, "responsavel": "Ana Pereira", "cliente": "Farmácia D", "data_pedido": "2023-10-04 13:00", "data_entrega": "2023-10-08 17:00", "data_vencimento": "2023-11-04 13:00" },
        { "id": 5, "responsavel": "Pedro Lima", "cliente": "Farmácia E", "data_pedido": "2023-10-05 14:00", "data_entrega": "2023-10-09 18:00", "data_vencimento": "2023-11-05 14:00" }
      ]
    }
  },
  methods: {
    teste() {
      console.log('teste aquuuii')
    }
  }
}
</script>

<style scoped>
/* Seu CSS aqui */
</style>
