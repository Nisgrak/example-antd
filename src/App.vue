<template>
  <a-select
      ref="select"
      v-model:value="value1"
      style="width: 120px"
      @focus="focus"
      @change="handleChange"
    >
      <a-select-option value="jack">Jack</a-select-option>
      <a-select-option value="lucy">Lucy</a-select-option>
      <a-select-option value="disabled" disabled>Disabled</a-select-option>
      <a-select-option value="Yiminghe">yiminghe</a-select-option>
    </a-select>

    <a-menu v-model:selectedKeys="current" mode="horizontal">
    <a-menu-item key="mail">
      <template #icon>
        <mail-outlined />
      </template>
      Navigation One
    </a-menu-item>
    <a-menu-item key="app" disabled>
      <template #icon>
        <appstore-outlined />
      </template>
      Navigation Two
    </a-menu-item>
    <a-sub-menu>
      <template #icon>
        <setting-outlined />
      </template>
      <template #title>Navigation Three - Submenu</template>
      <a-menu-item-group title="Item 1">
        <a-menu-item key="setting:1">Option 1</a-menu-item>
        <a-menu-item key="setting:2">Option 2</a-menu-item>
      </a-menu-item-group>
      <a-menu-item-group title="Item 2">
        <a-menu-item key="setting:3">Option 3</a-menu-item>
        <a-menu-item key="setting:4">Option 4</a-menu-item>
      </a-menu-item-group>
    </a-sub-menu>
    <a-menu-item key="alipay">
      <a href="https://antdv.com" target="_blank" rel="noopener noreferrer">
        Navigation Four - Link
      </a>
    </a-menu-item>
  </a-menu>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';


// This import of SelectOption directly works
import { Select as ASelect } from 'ant-design-vue';
import { SelectOption as ASelectOption } from "ant-design-vue/lib/select";
import "ant-design-vue/lib/select/style";

// This import of childrens of Menu didn't work
import { Menu as AMenu } from 'ant-design-vue';
import { MenuItem as AMenuItem, MenuItemGroup as AMenuItemGroup, SubMenu as ASubMenu } from "ant-design-vue/lib/menu";
import "ant-design-vue/lib/menu/style";


import { MailOutlined, AppstoreOutlined, SettingOutlined } from '@ant-design/icons-vue';

export default defineComponent({
  name: 'App',
  components: {
    ASelect,
    ASelectOption,


    AMenu,
    AMenuItem,
    AMenuItemGroup,
    ASubMenu,

  
    MailOutlined, AppstoreOutlined, SettingOutlined
  },
  setup() {
    const focus = () => {
      console.log('focus');
    };

    const handleChange = (value: string) => {
      console.log(`selected ${value}`);
    };

     const current = ref<string[]>(['mail']);

    return {
      focus,
      handleChange,
      value1: ref('lucy'),
      current
    };
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
