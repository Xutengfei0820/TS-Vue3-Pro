<template>
  <nav class="navbar navbar-dark bg-primary justify-content-between mb-4 px-4">
    <a class="navbar-brand" href="#">我的专栏</a>
    <ul v-if="!user.isLogin" class="list-inline mb-0">
      <li class="list-inline-item">
        <a class="btn btn-outline-light my-2" href="#">登录</a>
      </li>
      <li class="list-inline-item">
        <a class="btn btn-outline-light my-2" href="#">注册</a>
      </li>
    </ul>
    <ul v-else class="list-inline mb-0">
      <li class="list-inline-item">
        <!-- <a class="btn btn-outline-light my-2" href="#">你好 {{ user.name }}</a> -->
        <dropdown :title="`你好${user.name}`">
          <dropdown-item disabled>
            <a href="#" class="dropdown-item">新建文章</a>
          </dropdown-item>
          <dropdown-item>
            <a href="#" class="dropdown-item">编辑资料</a>
          </dropdown-item>
          <dropdown-item>
            <a href="#" class="dropdown-item">退出登录</a>
          </dropdown-item>
        </dropdown>
      </li>
    </ul>
  </nav>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue'
import Dropdown from './Dropdown.vue'
import DropdownItem from './DropdownItem.vue'
export interface UserProps {
  isLogin: boolean
  name?: string
  id?: string
}
export default defineComponent({
  name: 'GlobalHeader',
  components: {
    Dropdown,
    DropdownItem
  },
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true
    }
  }
})
</script>
