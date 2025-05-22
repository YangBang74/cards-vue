<template>
  <div class="container">
    <div class="top">
      <SelectedItems :items="selectedUsers" />
      <SelectedItem :item="selectedChoice" />
    </div>
    <div class="bottom">
      <ItemList
        :items="userItems"
        :multiple="true"
        :maxSelection="6"
        :selected="selectedUsers"
        @update:selected="onUserSelect"
      />
      <ItemList
        :items="choiceItems"
        :multiple="false"
        :selected="selectedChoice"
        @update:selected="onChoiceSelect"
      />
    </div>
  </div>
</template>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.top,
.bottom {
  display: flex;
  flex: 1;
}
.top > *,
.bottom > * {
  flex: 1;
  border: 1px solid #ccc;
  margin: 8px;
  padding: 8px;
}
</style>
