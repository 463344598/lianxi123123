<template>
    <div class="Ttop" style="background-color: #fff;">

      <div>发现</div>
     <!-- <home-list :zt="st" :se="selected"></home-list>-->
<div class="bottom1"></div>
    </div>
</template>

<script type="text/ecmascript-6">
  import {foodMenu ,zhufang1,zhufang2,zhufang3,zhufang4} from '../../ajax/ajax'
  import {mapState,mapMutations} from 'vuex'
  import {setStore, getStore} from '../../config/mUtils'
  import connect from '../../store/connect'
  export default {
    data () {
      return {
        selected:"1",
        topStatus: '',
        sj1:[],
        sj2:[],
        sj3:[],
        sj4:[],
        st:'q1',
        msg1:'homelist',
        frontPoints: 0,
        msgg:"",
        ele:"",
        enum1:getStore('num')||0,
      }
    },
    created(){

      /*this.GET_gNUM()*/

     // console.log(this.xname);
      connect.$on('name1',num1=>{
        this.msg1=num1
      })
      connect.$on('id1',num2=>{
        console.log(num2);
        this.msgg=num2
      })
      connect.$on('ele',num3=>{
        console.log(num3);
        this.ele=num3
      })
      connect.$on('nums',num4=>{
        console.log(num4);
        this.enum1=num4;
      })

       /*
       connect.$on('id1',num=>{// 箭头函数可以this指向全局this
        //  this.pickNum=prodTools.getTotalCount();
       // this.msg1=num;
         console.log(num);
      })*/
    },
    computed: {
      ...mapState([
        'xname','xele','xnums'
      ]),
      ...mapMutations([
        'GET_NAME','GET_NAME1'
      ]),

    },
    methods: {

      tab1(){
        zhufang1().then(res=>{this.sj1=res.data.data.list})
        this.selected="1"
        this.st='q1'
        this.msg1='homelist'
        console.log(this.xname);
       // this.GET_NAME1(this.xname)
        this.$store.state.xname='homelist'
      },
      tab2(){
        zhufang2().then(res=>{this.sj2=res.data.data.list})
        this.selected="2"
        this.st='q2'
        this.msg1='homelist'
        this.$store.state.xname='homelist'
      },
      tab3(){
        zhufang3().then(res=>{this.sj3=res.data.data.list})
        this.selected="3"
        this.st='q3'
        this.msg1='homelist'
        this.$store.state.xname='homelist'
      },
      tab4(){
        zhufang4().then(res=>{this.sj4=res.data.data.list})
        this.selected="4"
        this.st='q4'
        this.msg1='homelist'
        this.$store.state.xname='homelist'

      },

      /* loadBottom(){
        if(this.selected==1){
          console.log('上啦');
          this.$refs.loadmore.onBottomLoaded();
          this.load1();
        }else if(this.selected==2){
          console.log('上啦');
          this.$refs.loadmore.onBottomLoaded();
          this.load2();
        }else if(this.selected==3){
          console.log('上啦');
          this.$refs.loadmore.onBottomLoaded();
          this.load3();
        }else if(this.selected==4){
          console.log('上啦');
          this.$refs.loadmore.onBottomLoaded();
          this.load4();
        }

      },
      load1(){
        zhufang1().then(res=>{this.sj1=[...this.sj1,...res.data.data.list];/!* this.sj=this.sj.concat(res.data.contents);*!/})

      },
      load2(){
        zhufang2().then(res=>{this.sj2=[...this.sj2,...res.data.data.list];/!* this.sj=this.sj.concat(res.data.contents);*!/})

      },
      load3(){
        zhufang3().then(res=>{this.sj3=[...this.sj3,...res.data.data.list];/!* this.sj=this.sj.concat(res.data.contents);*!/})

      },
      load4(){
        zhufang4().then(res=>{this.sj4=[...this.sj4,...res.data.data.list];/!* this.sj=this.sj.concat(res.data.contents);*!/})

      },
      handleTopChange(status) { console.log(11);
        this.topStatus = status;
      },*/

    },
    watch:{
      frontPoints(newValue, oldValue) {
        console.log(newValue)
      },
     /* msg1: function (val, oldVal) {
        console.log('new: %s, old: %s', val, oldVal)
        this.msg1=123123
      },*/
    }
  }
</script>
<style lang="less">
.mui-card-footer span{ font-size: 15px;}
  .mint-loadmore{ width: 100%;}
.mui-card{    box-shadow: 0 1px 5px rgba(0,0,0,0.2);}

</style>
