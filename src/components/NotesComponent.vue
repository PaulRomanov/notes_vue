<template>
  <div>
    <h1>Список заметок</h1>
    <input
      type="text"
      class="custom-input"
      v-model="valueModel"
      @keypress.enter="addNewNote"
    />
    <ul class="note-list" v-if="notes.length !== 0">
      <li class="note-item" v-for="(note, index) in notes" :key="index">
        {{ note }}
        <button @click="removeNote(index)" class="remove-button">Удалить</button>
      </li>
    </ul>
    <div v-else>Введите новую заметку</div>
    <hr />
    <button @click="addNewNote" class="add-button">Добавить заметку</button>
  </div>
</template>

<script>
export default {
  name: "NotesComponent",
  data() {
    return {
      notes: ["заметка 1", "заметка 2", "заметка 3"],
      valueModel: "",
    };
  },
  methods: {
    addNewNote() {
      if (this.valueModel !== "") {
        this.notes.push(this.valueModel);
        this.valueModel = "";
      }
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.custom-input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 100%;
  margin-bottom: 10px;
}

.note-list {
  list-style-type: none;
  padding: 0;
}

.note-item {
  display: flex;
  align-items: center;
  margin-bottom: 5px;
}

.add-button {
  background-color: green;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  margin-right: 10px;
}

.remove-button {
  background-color: red;
  color: white;
  border: none;
  padding: 5px 10px;
  font-size: 12px;
  cursor: pointer;
  margin-left: 10px;
}
</style>
