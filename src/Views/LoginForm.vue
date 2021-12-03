<template>
    <div class="container">
        <form>
                <h1> Log in </h1>
                 <Form v-model="email" :placeHolder="'email'"  class="inputWidth" :inputType="'email'" />
                <Form v-model="password"  :placeHolder="'password'"  :inputType="'password'" />
                <Button :textBtn="'Login'" style="width:192%" />
        </form>
    </div>
</template>

<script>

import Form from '../components/Form.vue'
import Button from '../components/Button.vue'
import axios from 'axios';

export default {
    name: 'LoginForm',
    components: {
        Form,
        Button
    },
    methods: {
          login(user) {
    return axios
      .post('API_URL' + 'signin', {
        username: user.username,
        password: user.password
      })
      .then(response => {
        if (response.data.accessToken) {
          localStorage.setItem('user', JSON.stringify(response.data));
        }

        return response.data;
      });
    }
}
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@500&family=Montserrat:ital@1&family=Poppins:wght@300;400;500;600;700&display=swap');

 form {
     padding:12em;
 }


.container {
                font-family: 'Montserrat', sans-serif;

    display: flex;
    justify-content: center;
    box-shadow: 3px -1px 32px 7px rgba(0,0,0,0.2);
        -webkit-box-shadow: 3px -1px 32px 7px rgba(0,0,0,0.2);
        -moz-box-shadow: 3px -1px 32px 7px rgba(0,0,0,0.2);
}

 .inputWidth {
     width:25em;
 }


</style>