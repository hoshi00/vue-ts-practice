<template>

<div>
  <list-title></list-title>
  <ul>
    <li v-for="user in users" :key="user.id" @click='selected_user = user'>
      {{ user.name }}
    </li>
  </ul>
  <user-detail :user='selected_user'></user-detail>
</div>

</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import UserDetail from "@/components/UserDetail.vue";

  @Component({
    components: {
      UserDetail,
    },
  })
  export default class UserList extends Vue {
    public users: [
      {id: number = 1, name: string = 'ユーザー１'},
      {id: number = 2, name: string = 'ユーザー2'}
    ]
    public selected_user: string = {}
  }
</script>

<template>
  <button @click="onClick">MyButton</button>
</template>

<script lang="ts">
  import { Component, Emit, Prop, Vue } from 'vue-property-decorator';
  @Component
  export default class MyButton extends Vue {
    @Prop()
    public greet?: string;

    @Emit()
    public clicked() {
      alert('こんにちわ')
    }

    public onClick() {
      alert(this.greet)
      this.clicked();
    }
  }
</script>