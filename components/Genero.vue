<template>
    <div>
        <div class="btt-label" v-if="gameGenre">
            <div class="label sec-p">{{ gameGenre }}</div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  props: {
        buttonText: {
            type: String,
            default: '{{generoText}}'
        }},
};
</script>

<style scoped>
.label {
    color: var(--100);
    word-wrap: break-word;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
  }
  .btt-label {
  padding: 5px 10px;
  background: var(--700);
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
}
</style>
