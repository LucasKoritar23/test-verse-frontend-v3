<template>
    <b-container>
        <b-row align-v="center">
            <TableComponent />
        </b-row>
    </b-container>
</template>

<script>

import TableComponent from '@/components/TableComponent.vue'

export default {
    name: 'ListarSuites',
    components: {
        TableComponent
    }
}
</script>