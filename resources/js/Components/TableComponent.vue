<template>
    <table class="w-full border-collapse rounded-xl">
        <thead>
            <tr class="rounded-sm bg-slate-950 text-white uppercase text-sm">
                <th v-for="column in columns" :key="column.key" class="py-3 px-6 text-left">
                    {{ column.label }}
                </th>
            </tr>
        </thead>
        <tbody class="text-gray-800 text-sm">
            <tr v-for="row in rows" :key="row.id"
                class="border-b border-gray-200 hover:bg-slate-700 transition duration-200 hover:text-gray-100">
                <td v-for="column in columns" :key="column.key" class="py-3 px-6">
                    {{ row[column.key] }}
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: {
        columns: Array,
        rows: Array
    }
};
</script>