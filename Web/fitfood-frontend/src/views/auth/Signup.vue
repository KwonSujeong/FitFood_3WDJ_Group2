/* 회원가입 페이지 */

<template>
    <v-layout justify-center>
        <v-flex xs12 sm12 md12 class="pa-5">
                <div class="display-1 green--text font-weight-bold" style="margin-bottom:30px; text-align:center;">
                    SIGNUP
                </div>
        
                <v-form>
                    <span>
                    <v-layout justify-center>
                        <v-flex xs12 sm8 md6>
                            <v-text-field
                                type="email" label="아이디(이메일)" v-model="email" :rules="emailRules" required>
                            </v-text-field>
                            <v-text-field
                                type="password" label="비밀번호" counter="6" v-model="password" :rules="passwordRules" required>
                            </v-text-field>           
                            <v-text-field
                                type="password" label="비밀번호 확인" counter="6" v-model="password_ok" :rules="password_okRules" required>
                            </v-text-field>
                            <v-text-field
                                type="input" label="이름" v-model="name" :rules="nameRules" required>
                            </v-text-field>
                        </v-flex>  
                    </v-layout>

                    <v-layout justify-center>
                        <v-btn-toggle v-model="gender">
                            <v-btn
                                depressed text :value="1"
                                class="pl-4 pb-5 pr-4 pt-2 font-weight-bold title"
                                style="width:250px;">
                                <span stlyle="line-height:40px;">남자</span>
                            </v-btn>

                            <v-btn
                                depressed text :value="2"
                                class="pl-4 pb-5 pr-4 pt-2 font-weight-bold title"
                                style="width:250px;">
                                <span stlyle="line-height:40px;">여자</span>
                            </v-btn>
                        </v-btn-toggle>
                    </v-layout>

                    <v-layout class="mt-4 mb-4" justify-center >
                        <v-flex xs6 sm4 md3 style="margin-right:20px;">
                            <v-text-field
                                type="input" label="신장" v-model="Height" :rules="HeightRules" required>
                            </v-text-field>
                        </v-flex>
                        <v-flex xs6 sm4 md3>
                            <v-text-field
                                type="input" label="체중" v-model="Weight" :rules="WeightRules" required>
                            </v-text-field>
                        </v-flex>
                    </v-layout>

                    <v-layout justify-center>
                        <v-flex xs12 sm8 md6>         
                                <v-menu
                                    ref="menu"
                                    v-model="menu"
                                    :close-on-content-click="false"
                                    transition="scale-transition"
                                    offset-y
                                    min-width="290px"
                                >
                                    <template v-slot:activator="{ on }">
                                    <v-text-field
                                        v-model="date"
                                        label="생년월일"
                                        v-on="on"
                                    ></v-text-field>
                                    </template>
                                    <v-date-picker
                                    ref="picker"
                                    v-model="date"
                                    :max="new Date().toISOString().substr(0, 10)"
                                    min="1950-01-01"
                                    @change="save"
                                    ></v-date-picker>
                                </v-menu>
                        </v-flex>

                            <!-- <template>
                                <v-row justify="center">
                                    <v-date-picker v-model="day" color="green lighten-1"></v-date-picker>
                                </v-row>
                            </template> -->                    
                    </v-layout>

                        <v-card-actions>
                            <v-layout row wrap justify-center style="margin-top:30px;">
                                <v-flex xs12 sm8 md6>
                                    <v-btn
                                        type="submit" form="check-register-form"
                                        color="success" large block
                                        class="headline font-weight-bold mt-3">
                                        회원가입
                                    </v-btn>
                                </v-flex>
                            </v-layout>
                        </v-card-actions>
                    </span>
                </v-form>


        </v-flex>
    </v-layout>
</template>

<script>

export default {   
    name: 'signup',
    data(){
        return{
            email:'', //이메일
            emailRules: [
            v => !!v || '이메일을 입력해 주세요!', 
            v => /.+@.+/.test(v) || '메일 형식으로 입력해 주세요!' 
            ],
            password:'', //비밀번호
            passwordRules: [
            v => !!v || '패스워드를 입력해 주세요!',
            v => v.length >= 6 || '6글자이상 입력해 주세요!'
            ],
            name:'', //이름
            nameRules: [
            v => !!v || '이름을 입력해 주세요!',
            ],
            password_ok:'', //비밀번호 확인
            password_okRules:[
                v => v == this.password || '일치하지 않습니다!' 
            ],
            phone:'', //핸드폰
            gender: this.gender, //성별
            //gender:0, //성별
            Height:'',//신장
            HeightRules: [
            v => !!v || '신장을 입력해 주세요!',
            ],
            Weight:'',//체중
            WeightRules: [
            v => !!v || '체중을 입력해 주세요!',
            ],
            menu:false,
            date:null, //생년월일
            
            }
    },
    watch: {
      menu (val) {
        val && setTimeout(() => (this.$refs.picker.activePicker = 'YEAR'))
      },
    },
    //  methods: {
    //     register(){
    //         axios.post('/api/register',
    //         {
    //             name: this.name,
    //             email: this.email,
    //             password: this.password
    //         })
    //         .then((res) => {
    //             console.log(res)
    //             router.push({ name: 'Login' })
    //         })
    //         .catch((err) => {
    //             console.log(err)
    //         })
    //     },
    //     save (date) {
    //         this.$refs.menu.save(date)
    //     },
    // },
    methods: {
      save (date) {
        this.$refs.menu.save(date)
      },
    },
    //핸드폰 숫자만 입력가능
    //  watch:{
    //         phone(){
    //         return this.phone = this.phone.replace(/[^0-9]/g, '');
    //                 }
    //         },
}
</script>