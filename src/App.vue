<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <h3>گزارش تخلفات</h3>
                    <hr>
                    <div class="form-group">
                        <label for="email">ایمیل</label>
                        <input
                                type="text"
                                id="email"
                                class="form-control"
                                :value="userData.email"
                                @input="userData.email = $event.target.value"
                        >
                    </div>
                    <div class="form-group">
                        <label for="password">رمز عبور</label>
                        <input
                                type="password"
                                id="password"
                                class="form-control"
                                v-model.lazy="userData.password"
                        >
                      {{userData.password}}
                    </div>
                    <div class="form-group">
                        <label for="age">سن</label>
                        <input
                                type="number"
                                id="age"
                                class="form-control"
                                v-model="userData.age"
                        >
                    </div>

                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="message">پیام</label><br>
                    <textarea
                            id="message"
                            rows="5"
                            class="form-control"
                            v-model="message"
                    ></textarea>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <div class="form-group">
                        <label for="sendmail">
                            <input
                                    type="checkbox"
                                    id="sendmail"
                                    value="ارسال ایمیل"
                                    v-model="sendMail"
                            > ارسال ایمیل
                        </label>
                        <label for="sendInfomail">
                            <input
                                    type="checkbox"
                                    id="sendInfomail"
                                    value="ارسال اطلاعات ایمیل"
                                    v-model="sendMail"
                            > ارسال اطلاعات ایمیل
                        </label>
                    </div>

                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
                    <label for="male">
                        <input
                                type="radio"
                                id="male"
                                value="مرد"
                                v-model="gender"
                        > مرد
                    </label>
                    <label for="female">
                        <input
                                type="radio"
                                id="female"
                                value="زن"
                                v-model="gender"
                        > زن
                    </label>
                </div>
            </div>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
                    <label for="priority">سطح شکایت</label>
                    <select
                            id="priority"
                            class="form-control"
                            v-model="selectedPriority"
                    >
                        <option v-for="priority in priorities">{{priority}}</option>
                    </select>
                </div>
            </div>
            <div class="row">
              <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <app-switch
                    v-model="dataSwitch"
                ></app-switch>
              </div>
            </div>
            <hr>
            <div class="row">
                <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                    <button
                            class="btn btn-primary"
                            @click.prevent="submitted"
                    >ثبت
                    </button>
                </div>
            </div>
        </form>
        <hr>
        <div class="row" v-if="isSubmitted">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h4>اطلاعات درج شده</h4>
                    </div>
                    <div class="panel-body">
                        <p>ایمیل: {{userData.email}}</p>
                        <p>رمز عبور: {{userData.password}}</p>
                        <p>سن: {{userData.age}}</p>
                        <p style="white-space: pre">پیام: {{message}}</p>
                        <p><strong>ارسال ایمیل؟</strong></p>
                        <ul dir="rtl">
                            <li v-for="item in sendMail">{{item}}</li>
                        </ul>
                        <p>جنسیت: {{gender}}</p>
                        <p>سطح شکایت: {{selectedPriority}}</p>
                        <p>تغییرات: {{dataSwitch}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Switch from "./Switch.vue"
    export default {
      data(){
        return {
          userData:{
            email: '',
            password: '',
            age: ''
          },
          message: 'یک توضیح جدید',
          sendMail: [],
          gender: 'مرد',
          selectedPriority: 'اورژانسی',
          priorities: ['عادی', 'متوسط','اورژانسی'],
          dataSwitch: true,
          isSubmitted: false
        }
      },
      methods:{
        submitted(){
          this.isSubmitted = true;
        }
      },
      components: {
        appSwitch: Switch
      }
    }
</script>

<style>

</style>
