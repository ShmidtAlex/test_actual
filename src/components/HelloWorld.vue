<template>
  <div class="authorisation_block">
    <form class="authorisation_form" action="">
      <div class="up_content">
        <div class="caption_block">
          <p>авторизация пользователя</p>
        </div>     
        <div class="choose_action_block">
          <!-- можно реализовать через роутер? -->
          <input style="width: 56px" type="button" class="auth_enter" :class="{auth_enter_active: existUser }" value="вход" @click="newUser = false, existUser = true" >
          <input style="width: 120px" type="button" class="auth_enter" :class="{auth_enter_active: newUser }" value="регистрация" @click="newUser = true, existUser = false">
        </div>
      </div>
      <div class="low_content">
        <div v-if="existUser" class="enter_user-data_block">
          <ExistUser />
        </div>
        <div v-if="newUser" class="enter_user-data_block">
          <NewUser />
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import ExistUser from "@/components/ExistUserCase.vue";
import NewUser from "@/components/NewUserCase.vue";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    ExistUser,
    NewUser
  },
  data: function() {
    return {
      existUser: true,
      newUser: false
    }
  },
  methods: {
    showExistingAccaunt: function() {
      console.log("showExistingAccaunt");
    },
    registerNewAccaunt: function() {
      console.log("registerNewAccaunt");
    }
  }
};
</script>
<style scoped lang="less">
@media (min-width: 569px) {
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
  .authorisation_block {
    position: relative;
  }
  .authorisation_form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 470px;
    height: 370px;
    background: rgba(255, 255, 255, 0.7);
    border-radius: 4px;
    .up_content {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      height: 109px;
      width: 100%;
      .caption_block {
        margin-top: 22px;
        width: 100%;
        height: 32px;
        display: flex;
        justify-content: center;
        align-items: flex-start;
        p {
          font-family: Roboto;
          font-style: normal;
          font-weight: bold;
          font-size: 22px;
          text-align: center;
          text-transform: uppercase;
          color: #86764B;
          margin: 0;
          padding: 0;
        }
      }
      .choose_action_block {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: flex-start;
        width: 200px;
        height: 34px;
        margin-bottom: -24px;
        .auth_enter {
          border: none;
          background-color: transparent;
          font-family: Roboto;
          font-style: normal;
          font-weight: normal;
          font-size: 14px;
          height: 25px;
          text-align: center;
          text-transform: uppercase;
          color: #000000;
          width: auto;
          outline: none;
          border-bottom: 1px solid transparent;
          transform: scale(1, 0.95);
          display: flex;
          flex-direction: column;
          justify-content: flex-start;
          align-items: center;
        }
        .auth_enter_active {
          border-bottom: 1px solid #85754A;
          font-weight: 800;
        }
      }
    }
    .low_content {
      height: 258px;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
    }
    .enter_user-data_block {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 100%;
      border-top: 1px solid #E5E5E5;
    }
  }
}
@media (max-width: 568px) {
  .authorisation_block {
    position: static;
    width: 100vw;
  }
  .authorisation_form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    height: 370px;
    background: rgba(255, 255, 255, 0.7);
    border-radius: 4px;
    .up_content {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      height: 109px;
      width: 100%;
      .caption_block {
        margin-top: 22px;
        width: 100%;
        height: 32px;
        display: flex;
        justify-content: center;
        align-items: flex-start;
        p {
          font-family: Roboto;
          font-style: normal;
          font-weight: bold;
          font-size: 18px;
          // line-height: 47px;
          text-align: center;
          text-transform: uppercase;
          color: #86764b;
          margin: 0;
          padding: 0;
        }
      }
      .choose_action_block {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: flex-start;
        width: 200px;
        height: 34px;
        margin-bottom: -24px;
        .auth_enter {
          border: none;
          background-color: transparent;
          font-family: Roboto;
          font-style: normal;
          font-weight: normal;
          font-size: 14px;
          height: 25px;
          text-align: center;
          text-transform: uppercase;
          color: #000000;
          width: auto;
          outline: none;
          border-bottom: 1px solid transparent;
          transform: scale(1, 0.95);
          display: flex;
          flex-direction: column;
          justify-content: flex-start;
          align-items: center;
        }
        .auth_enter_active {
          border-bottom: 1px solid #85754a;
          font-weight: 800;
        }
      }
    }
    .low_content {
      height: 258px;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
    }
    .enter_user-data_block {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 100%;
      border-top: 1px solid #E5E5E5;
    }
  }
}



</style>
