<script setup>
import { ref } from 'vue'

import TableHeader from '@/pages/roles/TableHeader.vue'
import PermissionTable from '@/pages/roles/PermissionTable.vue'

// Исходные данные для таблицы
const rows = ref([
  { id: 1, name: 'Менеджмент', roles: ['Админ'], date: 1713073200 },
  { id: 2, name: 'Управление счетами', roles: ['Админ'], date: 1726453200 },
  { id: 3, name: 'Управление пользователями', roles: ['Админ', 'Менеджер'], date: 1728372000 },
  { id: 4, name: 'Управление рассылками', roles: ['Админ', 'Поддержка'], date: 1715677800 },
  {
    id: 5,
    name: 'Общение с клиентами',
    roles: ['Админ', 'Пользователь', 'Поддержка'],
    date: 1724367600,
  },
  { id: 6, name: 'Только просмотр', roles: ['Админ', 'Гость'], date: 1713169920 },
  { id: 7, name: 'Финансовый менеджмент', roles: ['Админ', 'Менеджер'], date: 1733289300 },
  {
    id: 8,
    name: 'Управлять задачами других людей',
    roles: ['Админ', 'Поддержка'],
    date: 1732544640,
  },
])

// Количество строк на странице
const rowsPerPage = ref(5)
const handleChangeRows = (newRowsPerPage) => (rowsPerPage.value = newRowsPerPage)

// Поиск по названию
const searchQuery = ref('')
const handleSearchQuery = (query) => (searchQuery.value = query)
</script>

<template>
  <div class="card">
    <div class="mb-3">
      <TableHeader @changeRowsPerPage="handleChangeRows" @searchRowData="handleSearchQuery" />
    </div>

    <PermissionTable
      :rows="rows"
      :headers="['Название', 'Роль', 'Дата', 'Действие']"
      :rowsPerPage="rowsPerPage"
      :searchQuery="searchQuery"
    />
  </div>
</template>

<style scoped lang="scss"></style>
