<template>
  <div :class="contentClasses">
    <PageContainer :is-full-width="device === 'mobile' ? true : false" :width="deviceWidth">
      <slot name="breadcrumbs"></slot>
      <h3>{{ $route.meta.title }}</h3>
      <slot></slot>
    </PageContainer>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import type { IPropsContent } from './PageContent.types';
import { toRefs } from 'vue';
import PageContainer from '../PageContainer/PageContainer.vue';
import { useMedia } from '@/composables/useMedia';

const props = withDefaults(defineProps<IPropsContent>(), {
  isDark: false
});

const { isDark } = toRefs(props);

const contentClasses = computed(() => {
  return { content: true, ['dark-content']: isDark.value };
});

const { device } = useMedia();

const deviceWidth = computed(() => {
  if (device.value === 'desktop') return 1200;
  if (device.value === 'tablet') return 700;
  return 700;
});
</script>

<style src="./PageContent.style.scss" lang="scss" scoped />
