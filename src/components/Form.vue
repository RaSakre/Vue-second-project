<template>
  <form @submit.prevent="emitAdd" class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select v-model="type" id="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="textarea" id="value" rows="3"></textarea>
    </div>

    <button :disabled="textarea.length < 3" class="btn primary">
      Добавить
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      type: "",
      textarea: "",
    };
  },
  methods: {
    emitAdd() {
      this.$emit("emitAdd", {
        type: this.type,
        value: this.textarea,
      });
      this.type = "title";
      this.textarea = "";
    },
  },
};
</script>

<style scoped></style>
