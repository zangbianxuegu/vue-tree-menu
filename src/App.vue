<script setup>
import { HomeIcon, NewspaperIcon, PhotoIcon } from "@heroicons/vue/24/outline";
import TreeMenu from "./components/TreeMenu";

const menuData = [
  {
    label: "一级菜单 1",
    active: false,
    icon: HomeIcon,
    children: [],
  },
  {
    label: "一级菜单 2",
    active: false,
    icon: NewspaperIcon,
    children: [
      {
        label: "二级菜单 1",
        active: false,
        children: [],
      },
      {
        label: "二级菜单 2",
        active: false,
        children: [],
      },
      {
        label: "二级菜单 3",
        active: false,
        children: [],
      },
    ],
  },
  {
    label: "一级菜单 3",
    active: false,
    icon: PhotoIcon,
    children: [
      {
        label: "二级菜单 1",
        active: false,
        children: [],
      },
      {
        label: "二级菜单 2",
        active: false,
        children: [],
      },
      {
        label: "二级菜单 3",
        active: false,
        children: [
          {
            label: "三级菜单 1",
            active: false,
            children: [],
          },
          {
            label: "三级菜单 2",
            active: false,
            children: [],
          },
          {
            label: "三级菜单 3",
            active: false,
            children: [
              {
                label: "四级菜单 1",
                active: true,
                children: [],
              },
            ],
          },
        ],
      },
    ],
  },
];
</script>

<template>
  <div class="flex min-h-screen">
    <nav class="w-64 shrink-0 bg-gray-50 border-r border-gray-200 py-4">
      <TreeMenu :data="menuData"></TreeMenu>
    </nav>
    <main class="p-4"></main>
  </div>
</template>
