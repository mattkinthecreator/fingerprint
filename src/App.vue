<script setup lang="ts">
import FingerprintJS from '@fingerprintjs/fingerprintjs';
import { onMounted, ref } from 'vue';

const fpPromise = FingerprintJS.load();

const resultRef = ref();

onMounted(async () => {
  const fp = await fpPromise;
  const result = await fp.get();
  resultRef.value = result;
});
</script>

<template>
  <pre>
    {{ JSON.stringify(resultRef, null, 2) }}
  </pre>
</template>

<style scoped></style>
