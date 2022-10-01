<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from "@headlessui/vue";
import { ChevronDownIcon } from "@heroicons/vue/24/solid";
import { computed } from "vue";
import TreeMenu from "./TreeMenu.vue";

const props = defineProps({
  item: Object,
});

const hasActive = computed(() => {
  function hasActiveItem(items) {
    if (!items || !items.length) {
      return false;
    }
    return items.some((item) => item.active || hasActiveItem(item.children));
  }
  return hasActiveItem(props.item.children);
});
</script>
<template>
  <a
    v-if="!item.children || !item?.children?.length"
    :class="[
      'group flex w-full rounded-md item-center py-2 px-3',
      'hover:bg-gray-100',
      item.active ? 'text-gray-800 font-semibold' : 'text-gray-600 font-medium',
    ]"
    href="#"
  >
    <component
      v-if="item.label"
      :is="item.icon"
      :class="[
        'w-6 h-6 shrink-0 mr-2 group-hover:text-gray-600',
        item.active ? 'text-gray-600' : 'text-gray-400',
      ]"
    ></component>
    <span>{{ item.label }}</span>
  </a>
  <Disclosure v-else v-slot="{ open }" :default-open="hasActive">
    <DisclosureButton
      :class="[
        'group text-left flex w-full rounded-md item-center py-2 px-3',
        'hover:bg-gray-100',
        open ? 'font-semibold text-gray-800' : 'font-medium text-gray-600',
      ]"
    >
      <component
        v-if="item.label"
        :is="item.icon"
        :class="[
          'w-6 h-6 shrink-0 mr-2 group-hover:text-gray-600',
          open ? 'text-gray-600' : 'text-gray-400',
        ]"
      ></component>
      <span class="flex-1">{{ item.label }}</span>
      <ChevronDownIcon
        :class="[
          'w-6 h-6 shrink-0',
          open ? '-rotate-180 text-gray-600' : 'text-gray-400',
        ]"
      />
    </DisclosureButton>
    <DisclosurePanel class="ml-4">
      <TreeMenu :data="item.children" />
    </DisclosurePanel>
  </Disclosure>
</template>
