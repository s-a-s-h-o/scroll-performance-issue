<template>
  <v-avatar size="6.482rem">
    <div class="outlined">
      <v-img :src="this.imageSrc" alt="Avatar" contain />
    </div>
  </v-avatar>
</template>

<script>
export default {
  props: {
    imageSrc: {
      type: String
    }
  }
}
</script>

<style scoped>
.outlined {
  border: 0.2143rem solid #efefef;
  overflow: hidden;
  border-radius: 50%;
  height: 6.482rem;
  width: 6.482rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>