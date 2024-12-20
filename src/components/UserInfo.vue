<template>
  <div class="card card-w70">
    <div v-for="el in elements" :key="el.id">
      <h1 v-if="el.type === 'title'">{{ el.value }}</h1>
      <div class="avatar" v-if="el.type === 'avatar'">
        <img :src="el.value" alt="Avatar" />
      </div>
      <h2 v-if="el.type === 'subtitle'">{{ el.value }}</h2>
      <p v-if="el.type === 'text'">{{ el.value }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    elements: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped></style>
