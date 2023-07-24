<template>
    <div>
        <b-table v-if="displayedItems.length > 0" striped hover :items="displayedItems" :fields="tableFields" responsive
            class="table-fixed-layout">
            <template #table-busy>
                Loading data...
            </template>
            <template #cell(id_suite)="data">
                {{ data.value }}
            </template>
            <template #cell(nome_suite)="data">
                {{ data.value }}
            </template>
            <template #cell(status_atual)="data">
                <b-icon v-if="data.value === 'success'" icon="check-circle-fill" variant="success"></b-icon>
                <b-icon v-else-if="data.value === 'new'" icon="info-circle-fill" variant="info"></b-icon>
                <b-icon v-else-if="data.value === 'failed'" icon="x-circle-fill" variant="danger"></b-icon>
                <b-icon v-else-if="data.value === 'blocked'" icon="exclamation-circle-fill" variant="warning"></b-icon>
                <b-icon v-else-if="data.value === 'running'" icon="circle" variant="info"></b-icon>
                {{ data.value }}
            </template>
            <template #cell(data_criacao)="data">
                {{ data.value }}
            </template>
            <template #cell(data_edicao)="data">
                {{ data.value }}
            </template>
        </b-table>
        <div v-else>Sem suites cadastradas</div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            items: [],
            displayedItems: [],
            currentPage: 1,
            totalPages: 1,
            pageSize: 50,
            totalItems: 0,
            tableFields: [
                // Add fields for each column in the table
                { key: "id_suite", label: "ID", thClass: "text-center", sortable: true },
                { key: "nome_suite", label: "Nome da Suite", thClass: "text-center", sortable: true },
                { key: "status_atual", label: "Status Atual", thClass: "text-center", sortable: true },
                { key: "data_criacao", label: "Data de Criação", thClass: "text-center", sortable: true },
                { key: "data_edicao", label: "Data de Edição", thClass: "text-center", sortable: true }
            ],
            maxNomeSuiteLength: 30 // Set the maximum number of characters for "nome_suite" here
        };
    },
    async mounted() {
        await this.fetchData();
    },
    computed: {
        processedItems() {
            return this.items.map(item => ({
                ...item,
                nome_suite: this.truncateText(item.nome_suite, this.maxNomeSuiteLength)
            }));
        }
    },
    methods: {
        async fetchData() {
            try {
                const response = await fetch(`http://192.168.0.17:3001/suites`);
                if (!response.ok) {
                    throw new Error('Failed to fetch data from the API.');
                }
                const data = await response.json();
                this.items = data.items; // Extracting the "items" array from the API response
                this.updateDisplayedItems();
            } catch (error) {
                console.error(error);
                // Handle error or show an error message to the user
            }
        },
        updateDisplayedItems() {
            this.displayedItems = this.processedItems;
        },
        truncateText(text, maxLength) {
            if (text.length > maxLength) {
                return text.substring(0, maxLength) + '...';
            }
            return text;
        }
    }
};
</script>
  
<style>  /* Apply styles to truncate text within the "Nome da Suite" column */
  .table-fixed-layout .text-center {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
  }
</style>
