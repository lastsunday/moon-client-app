<script>
import { Button ,NavBar,Form,Field  } from 'vant';
import { reactive } from 'vue';

export default {
  name: 'Home',
  components: {
    [Button.name]:Button,
    [NavBar.name]:NavBar,
    [Form.name]:Form ,
    [Field.name]:Field
  },
  setup(){
    const state = reactive({
      username: '',
      password: '',
    });

    const onSubmit = function(values) {
      console.log('submit', values);
    }
    return {state,onSubmit}
  }
}
</script>

<template>
  <div class="home">
    <van-nav-bar
      title="登录"
    />
    <van-form @submit="onSubmit">
      <van-field
        v-model="state.username"
        name="用户名"
        label="用户名"
        placeholder="用户名"
        :rules="[{ required: true, message: '请填写用户名' }]"
      />
      <van-field
        v-model="state.password"
        type="password"
        name="密码"
        label="密码"
        placeholder="密码"
        :rules="[{ required: true, message: '请填写密码' }]"
      />
      <div style="margin: 16px;">
        <van-button round block type="primary" native-type="submit">
          提交
        </van-button>
      </div>
    </van-form>
  </div>
</template>

