<template>
    <div class="myAccount">
        <m-header>
            <span slot="header-cont">我的账户</span>
        </m-header>
        <div class="mui-content">
            <div class="hd">
                <div class="tp">
                    <div class="txt mb">贷款余额（元）</div>
                    <div class="money mb">{{info.surplusAmount}}</div>
                    <div class="tip mb">*{{info.bondMoneyStr}}</div>
                </div>
                <div class="wbox bt-wrap">
                    <a class="item wbox-flex mui-navigate-right" href="">
                        <div class="txt">可用贷款余额（元）</div>
                        <span class="">{{info.surplusAmount - info.orderLockAmount}}</span>
                    </a>
                    <a class="item wbox-flex mui-navigate-right" href="">
                        <div class="txt">订单锁定余额（元）</div>
                        <span class="">{{info.orderLockAmount}}</span>
                    </a>
                </div>
            </div>
            <div class="bd">
                <ul class="list">
                    <li class="mui-table-view-cell">
                        <a class="mui-navigate-right" href="/recharge">
                            <i class="icon"></i>贷款充值
                        </a>
                    </li>
                    <li class="mui-table-view-cell my-bank-center" >
                        <a class="mui-navigate-right" :href="info.bindBank?'/mybank':'javascript:;'">
                            <i class="icon" style="background-position-y:-32px;"></i>我的银行卡
                        </a>
                    </li>
                    <li class="mui-table-view-cell">
                        <a class="mui-navigate-right" href="/settleBank">
                            <i class="icon" style="background-position-y:-60px;"></i>提现到银行卡
                        </a>
                    </li>
                    <li class="mui-table-view-cell">
                        <a class="mui-navigate-right" href="/settleList">
                            <i class="icon" style="background-position-y:-89px;"></i>提现记录
                        </a>
                    </li>
                    <li class="mui-table-view-cell">
                        <a class="mui-navigate-right" href="/doCharge">
                            <i class="icon" style="background-position-y:-115px;"></i>分店贷款转账
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
import mHeader from "base/header/header";
import { apiAccountInfo } from 'api/api'

export default {
    components:{
        mHeader
    },
    data(){
        return{
            info:{}
        }
    },
    created(){
        this._getAccountInfo()
    },
    methods:{
        _getAccountInfo(){
            apiAccountInfo().then((result) => {
                if(result.status){
                    this.info = result.data
                    console.log(result.data)
                }
            }).catch((err) => {
                
            });
        }
    }
}
</script>
<style>
.myAccount .hd {background-image: linear-gradient(45deg, #1bac44 0%, #03923d 100%);}
.myAccount .hd .tp{padding:30px 15px;height:140px;color:#fff;}
.myAccount .hd .tp .mb{margin-bottom:12px;}
.myAccount .hd .tp .txt{font:13px/20px PingFang-SC-Medium;}
.myAccount .hd .tp .money{font-size:32px;}
.myAccount .hd .tp .tip{font:12px/20px PingFang-SC-Medium;color:rgba(255,255,255,.5);}
.myAccount .hd .bt-wrap{border-top:1px solid rgba(255,255,255,.2);margin-right:-1px;}
.myAccount .hd .bt-wrap .item{padding:15px;font-size:16px;color:#fff;position:relative;border-right:1px solid rgba(255,255,255,.2);}
.myAccount .hd .bt-wrap .item .txt{font-size:13px;}
.myAccount .hd .bt-wrap .mui-navigate-right:after{right:5px;color:rgba(255,255,255,.4);font-size:20px;}
.myAccount .bd{padding:15px;}
.myAccount .bd .list{background-color:#fff;border-radius:5px;}
.myAccount .bd .list .mui-table-view-cell{padding:0;line-height:50px;}
.myAccount .bd .list .mui-table-view-cell>a:not(.mui-btn){margin:0;padding:0 15px;font-size:14px;color:#333;}
.myAccount .bd .list .mui-table-view-cell:after{left:0;background-color:#ddd;}
.myAccount .bd .list .mui-navigate-right:after{right:5px;font-size:20px;color:#ccc;}
.myAccount .bd .list .mui-navigate-right .icon{float:left;width:22px;height:22px;background: url(../../common/images/account-icon.png) no-repeat -3px -3px;background-size:28px;margin:14px 10px 0 0;}

</style>


