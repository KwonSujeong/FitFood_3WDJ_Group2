<template>
    <v-container>
        <v-layout>
            <v-flex>
                <h1 class="green--text font-weight-bold" style="text-align:center; font-family : 'MapoPeacefull';">RECOMMEND</h1>

                <div style="margin-top: 100px; text-align:center; font-family : 'MapoPeacefull';" v-if="check">
                    <h1 class="font-weight-bold"><strong class="success--text"> 아침 </strong> 식사하셨습니까?</h1>
                    <v-btn color="orange" class="mb-2 white--text" style="margin-right: 40px; margin-top:30px;" @click="breakfast_yes()">네</v-btn>
                    <v-btn color="orange" class="mb-2 white--text" style="margin-top:30px;" @click="breakfast_no()">아니요</v-btn>
                </div>

                <!-- 리스트 -->
                <div v-else>
                    <v-layout style="margin-top:80px;" justify-center>
                        <!-- 아침 리스트 -->
                        <v-flex xs12 sm10 md6 justify-center v-show="value==3">
                            <h2 class="orange--text font-weight-bold" style="text-align:center; font-family : 'MapoPeacefull';">아침</h2>
                
                            <div class="d-flex flex-wrap" xs1 sm3 md6 style="justify-content:center; margin-top:30px;">                   
                                <v-layout justify-center>
                                    <v-flex xs3 sm3 md12>
                                        <v-card class="d-flex flex-wrap" style="margin-top:30px;">
                                            <div v-for="(recommend,i) in breakfast" v-bind:key="`${i}-${recommend.id}`">              
                                                <v-card style="margin-top: 80px; height: 300px; width:400px; margin-right:25px; margin-left:25px; font-family : 'MapoPeacefull';">
                                                    <div v-if="break_mealkind == 0">
                                                        <router-link rounded :to="{ name: 'Detailed',params : {id: recommend.store_id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <div v-else-if="break_mealkind ==1">
                                                        <router-link rounded :to="{ name: 'Recipe',params : {id: recommend.id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <h1 class="black--text font-weight-bold" style="text-align:center; margin-top: 20px; font-family : 'MapoPeacefull';">{{recommend.recommend_name}}</h1>
                                                </v-card>
                                            </div>
                                        </v-card>
                                    </v-flex>
                                </v-layout>
                            </div>
                        </v-flex>

                        <!-- 점심 리스트 -->
                        <v-flex xs12 sm10 md6 justify-center v-show="value==3||value==2">
                            <h2 class="orange--text font-weight-bold" style="text-align:center; font-family : 'MapoPeacefull';">점심</h2>
                
                            <div class="d-flex flex-wrap" xs1 sm3 md6 style="justify-content:center; margin-top:30px;">                   
                                <v-layout justify-center>
                                    <v-flex xs3 sm3 md12>
                                        <v-card class="d-flex flex-wrap" style="margin-top:30px;">                   
                                            <div v-for="(recommend,i) in lunch" v-bind:key="`${i}-${recommend.id}`">              
                                                <v-card style="margin-top: 80px; height: 300px; width:400px; margin-right:25px; margin-left:25px; font-family : 'MapoPeacefull';">
                                                    <div v-if="lunch_mealkind == 0">
                                                        <router-link rounded :to="{ name: 'Detailed',params : {id: recommend.store_id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <div v-else-if="lunch_mealkind ==1">
                                                        <router-link rounded :to="{ name: 'Recipe',params : {id: recommend.id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <h1 class="black--text font-weight-bold" style="text-align:center; margin-top: 20px; font-family : 'MapoPeacefull';">{{recommend.recommend_name}}</h1>
                                                </v-card>
                                            </div>
                                        </v-card>
                                    </v-flex>
                                </v-layout>
                            </div>
                        </v-flex>

                        <!-- 저녁 -->
                        <v-flex xs12 sm10 md6 justify-center>
                            <h2 class="orange--text font-weight-bold" style="text-align:center; font-family : 'MapoPeacefull';">저녁</h2>
                
                            <div class="d-flex flex-wrap" xs1 sm3 md6 style="justify-content:center; margin-top:30px;">                   
                                <v-layout justify-center>
                                    <v-flex xs3 sm3 md12>
                                        <v-card class="d-flex flex-wrap" style="margin-top:30px;">                   
                                            <div v-for="(recommend,i) in dinner" v-bind:key="`${i}-${recommend.id}`">              
                                                <v-card style="margin-top: 80px; height: 300px; width:400px; margin-right:25px; margin-left:25px; font-family : 'MapoPeacefull';">
                                                    <div v-if="dinner_mealkind == 0">
                                                        <router-link rounded :to="{ name: 'Detailed',params : {id: recommend.store_id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <div v-else-if="dinner_mealkind ==1">
                                                        <router-link rounded :to="{ name: 'Recipe',params : {id: recommend.id}}">
                                                        <v-img height="300px" width="400px" :src="recommend.image"></v-img>
                                                        </router-link>
                                                    </div>
                                                    <h1 class="black--text font-weight-bold" style="text-align:center; margin-top: 20px; font-family : 'MapoPeacefull';">{{recommend.recommend_name}}</h1>
                                                </v-card>
                                            </div>
                                        </v-card>
                                    </v-flex>
                                </v-layout>
                            </div>
                        </v-flex>
                    </v-layout>
                </div>

                <v-dialog v-model="dialog1" persistent max-width="400px">
                    <v-card>
                        <div>
                            <v-card-title class="justify-center"> 
                            <span class="headline orange--text font-weight-bold" style="margin-top:20px; font-family : 'MapoPeacefull';">아침으로 무엇을 드셨나요?</span>
                            </v-card-title>

                            <v-card-text>
                                <v-container>
                                    <v-row>
                                        <v-col cols="12">
                                            <v-text-field v-model="break_input" style="font-family : 'MapoPeacefull';" label="무엇을 드셨나요?" required></v-text-field>
                                        </v-col>

                                        <v-flex>
                                            <h2 class="green--text font-weight-bold" style="text-align:center; margin-top:20px; font-family : 'MapoPeacefull';">점심은 어떻게 드실건가요?</h2>
                                            
                                            <v-layout justify-center>
                                                <v-radio-group row v-model="lunch_mealkind" class="justify-center">
                                                    <v-radio label="식당" style="font-family : 'MapoPeacefull';" color="success" value="0"></v-radio>
                                                    <v-radio label="레시피" style="font-family : 'MapoPeacefull';" color="success" value="1"></v-radio>
                                                </v-radio-group>
                                            </v-layout>
                                        
                                            <h2 class="green--text font-weight-bold" style="text-align:center; margin-top:20px; font-family : 'MapoPeacefull';">저녁은 어떻게 드실건가요?</h2>
                                            
                                            <v-layout justify-center>
                                                <v-radio-group row v-model="dinner_mealkind" class="justify-center">
                                                    <v-radio label="식당" style="font-family : 'MapoPeacefull';" color="success" value="0" ></v-radio>
                                                    <v-radio label="레시피" style="font-family : 'MapoPeacefull';" color="success" value="1"></v-radio>
                                                </v-radio-group>
                                            </v-layout>
                                        </v-flex>
                                    </v-row>
                                </v-container>

                                <v-card-actions>
                                <div class="flex-grow-1"></div>
                                <v-btn color="orange darken-1" style="font-family : 'MapoPeacefull';" text @click="save()">확인</v-btn>
                                <v-btn color="orange darken-1" style="font-family : 'MapoPeacefull';" text @click="close()">취소</v-btn>
                                </v-card-actions>
                            </v-card-text>        
                        </div>                                              
                    </v-card>
                </v-dialog>

                <v-dialog v-model="dialog2" persistent max-width="400px">
                    <v-card>
                        <div>
                            <v-card-text>
                                <v-container>
                                    <v-row>
                                        <v-flex>
                                            <h2 class="green--text font-weight-bold" style="text-align:center; margin-top:20px; font-family : 'MapoPeacefull';">아침은 어떻게 드실건가요?</h2>
                                            
                                            <v-layout justify-center>
                                                <v-radio-group row v-model="break_mealkind" class="justify-center">
                                                    <v-radio label="식당" style="font-family : 'MapoPeacefull';" color="success" value="0"></v-radio>
                                                    <v-radio label="레시피" style="font-family : 'MapoPeacefull';" color="success" value="1"></v-radio>
                                                </v-radio-group>
                                            </v-layout>

                                            <h2 class="green--text font-weight-bold" style="text-align:center; margin-top:20px; font-family : 'MapoPeacefull';">점심은 어떻게 드실건가요?</h2>
                                            
                                            <v-layout justify-center>
                                                <v-radio-group row v-model="lunch_mealkind" class="justify-center">
                                                    <v-radio label="식당" style="font-family : 'MapoPeacefull';" color="success" value="0"></v-radio>
                                                    <v-radio label="레시피" style="font-family : 'MapoPeacefull';" color="success" value="1"></v-radio>
                                                </v-radio-group>
                                            </v-layout>
                                        
                                            <h2 class="green--text font-weight-bold" style="text-align:center; margin-top:20px; font-family : 'MapoPeacefull';">저녁은 어떻게 드실건가요?</h2>
                                            
                                            <v-layout justify-center>
                                                <v-radio-group row v-model="dinner_mealkind" class="justify-center">
                                                    <v-radio label="식당" style="font-family : 'MapoPeacefull';" color="success" value="0" ></v-radio>
                                                    <v-radio label="레시피" style="font-family : 'MapoPeacefull';" color="success" value="1"></v-radio>
                                                </v-radio-group>
                                            </v-layout>
                                        </v-flex>
                                    </v-row>
                                </v-container>

                                <v-card-actions>
                                <div class="flex-grow-1"></div>
                                <v-btn color="orange darken-1" style="font-family : 'MapoPeacefull';" text @click="save()">확인</v-btn>
                                <v-btn color="orange darken-1" style="font-family : 'MapoPeacefull';" text @click="close()">취소</v-btn>
                                </v-card-actions>
                            </v-card-text>        
                        </div>                                              
                    </v-card>
                </v-dialog>

            </v-flex>
        </v-layout>
    <br>
    <br>
    <br>
    <br>
    <br>

    </v-container>
</template>
<script>
import axios from 'axios'
import { mdiConsoleLine } from '@mdi/js'

export default {
	name: 'RecommendMain',
	data() {
        return {
            dialog1: false, //아침 먹었을 때
            dialog2: false, //아침 안 먹었을 때 
            recommends: [],
            user_id : "",
            break_input:'', //아침 밥 입력 값
            break_mealkind:"0", //다이얼 창 아침 라디오 버튼
            lunch_mealkind:"0", //다이얼 창 점심 라디오 버튼
            dinner_mealkind:"0", //다이얼 창 저녁 라디오 버튼
            check:true,
            mealKind: "", //아점저 식당 레시피 0,0,0 보낼때는 kind로 보낼것
            // mealKind: "", //아점저 체크
            value:"", // 3이면 아점저, 2면 점저
            breakfast:[], //아침밥 추천값
            lunch:[], // 점심밥 추천값
            dinner:[], // 저녁밥 추천값
        }
    },
    methods: {
        breakfast_yes(){
            this.dialog1 = true;
            this.value=2;
        },
        breakfast_no(){
            this.dialog2 = true;
            this.value=3;
            // this.mealKind = "0,0,0";
            console.log("아침 안 먹음");
        },
        save(){
            console.log("세이브 버튼 눌림")
            // this.mealKind ="0,0,0";
            this.dialog1 = false;
            this.dialog2 = false;
            this.check= false;

            axios.post('/saveBreak',{   // foods에서 사용자가 먹은 음식 이름 토대로 정보 검색 후 foodeatens에 저장
                food_name: this.break_input,
            })
            .then(res => {
                console.log(res);
            })
            .catch(err => {
                console.log("실패", err);
            })

            this.mealKind = "";
            console.log("아침, 점심, 저녁 : ",this.break_mealkind,this.lunch_mealkind,this.dinner_mealkind);
            this.mealKind += String(this.break_mealkind+","+this.lunch_mealkind+","+this.dinner_mealkind); 
            
            var formData = new FormData();
            formData.append('kind',this.mealKind);
            axios.post('http://127.0.0.1:5000/recommend/'+this.user_id,formData,{
            headers: {'Access-Control-Allow-Origin':'*'},
            })
            .then((res)=>{
            this.recommends = res.data.recommendMeals;
            console.log("데이터",this.recommends);
            this.recommends.forEach(arr =>{
                if(this.break_mealkind == 1){
                    arr[0].id = Math.abs(arr[0].id);
                }
                this.breakfast.push(arr[0]);
                if(this.lunch_mealkind == 1){
                    arr[1].id = Math.abs(arr[1].id);
                }
                this.lunch.push(arr[1]);
                if(this.dinner_mealkind == 1){
                    arr[2].id = Math.abs(arr[2].id);
                }
                this.dinner.push(arr[2]);
            })
            console.log("아침",this.breakfast);
            console.log("점심",this.lunch);
            console.log("저녁",this.dinner);
            })
            .catch((err)=>{
                console.log("실패",err)
            })
        },
        close(){
        this.dialog1 = false;
        this.dialog2 = false;
        },
    },
        computed :{
        },
        created:function(){
            axios.get('/show/'+localStorage.getItem('current_user'))
            .then(res=>
                {
                this.user_id=res.data.user_id;
                console.log('유저 아이디: ',this.user_id);
                })
        .catch(err=>console.error(err))

    },
    
}
</script>

<style scoped>
@font-face { font-family: 'MapoPeacefull'; src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/MapoPeacefullA.woff') format('woff'); font-weight: normal; font-style: normal; }
</style>