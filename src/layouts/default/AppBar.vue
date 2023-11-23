<template>

</template>

<script lang="ts" setup>

import {computed, ref} from "vue";
import {useStore} from "vuex";

const store = useStore();
const searchMessage = ref('');
const hasMessage = computed(() => searchMessage.value.length > 0)
const loading = computed(() => store.state);

function onSubmit() {
  if (hasMessage.value || loading.value) {
    store.dispatch('words/loadList', {query: searchMessage.value})
  }
}

</script>
