<template>
<div class="zc-order">
    <div class="zc-line-1">
        <div class="zc-user-name">{{order.customerName}}</div>
        <!-- <div class="zc-user-address">{{order.userAddress}}</div> -->
    </div>
    <div class="zc-line-2">
        <div class="zc-order-shop">{{order.store.name}}</div>
        <div class="zc-order-status">{{Status.zc[order.status].name}}</div>
    </div>
    <div class="zc-line-3">
        <div class="zc-butler-img"><img :src="order.manager.profileImage"></div>
        <div class="zc-butler-name">{{order.manager.nickname}}</div>
        <div class="zc-butler-tel" onclick="location.href='tel:{{order.manager.mobile}}'"><img src="../assets/images/tel.png"></div>
    </div>
    <div class="zc-line-4" v-if="order.status > 0">
        <div class="zc-count">退款金额<span>{{order.customerRefundAmount|currency "￥" 2}}</span></div>
    </div>
</div>
</template>

<script>
import Status from '../status'
export default {
    data() {
        return {
            Status
        }
    },
    components: {},
    methods: {
        getTime(timeStamp) {
            var d = new Date(timeStamp * 1000);
            var Y = d.getFullYear() + '-';
            var M = (d.getMonth() + 1 < 10 ? '0' + (d.getMonth() + 1) : d.getMonth() + 1) + '-';
            var D = (d.getDate() < 10 ? '0' + (d.getDate()) : d.getDate());
            return Y + M + D
        }
    },
    props: {
        data: {
            type: Object,
            default: {}
        },
        role: {
            type: String,
            default: 'user'
        }
    },
    computed: {
        order() {
            return this.data
        }
    }
}
</script>

<style scoped lang="less">
.zc-order {
    width: 100%;
    height: auto;
    background-color: #fff;
    margin-bottom: 10px;
    .zc-line-1 {
        height: 50px;
        width: 100%;
        border-bottom: 1px solid #eee;
        position: relative;
        .zc-user-name {
            position: absolute;
            top: 6px;
            left: 15px;
            font-size: 16px;
            color: #393939;
        }
    }
    .zc-line-2 {
        height: 40px;
        width: 100%;
        border-bottom: 1px solid #eee;
        position: relative;
        .zc-order-shop {
            position: absolute;
            top: 0;
            left: 15px;
            height: 40px;
            line-height: 40px;
            font-size: 14px;
            color: #393939;
        }
        .zc-order-status {
            position: absolute;
            right: 15px;
            top: 15px;
            font-size: 12px;
            color: #393939;
        }
    }
    .zc-line-3 {
        height: 50px;
        width: 100%;
        border-bottom: 1px solid #eee;
        position: relative;
        .zc-butler-img {
            position: absolute;
            top: 5px;
            left: 15px;
            height: 40px;
            width: 40px;
            border-radius: 20px;
            img {
                height: 100%;
                width: 100%;
                border-radius: 50%;
            }
        }
        .zc-butler-name {
            position: absolute;
            bottom: 15px;
            left: 65px;
            font-size: 16px;
            color: #393939;
        }
        .zc-butler-tel {
            position: absolute;
            top: 15px;
            right: 15px;
            height: 20px;
            width: 20px;
            img {
                height: 100%;
                width: 100%;
            }
        }
    }
    .zc-line-4 {
        position: relative;
        height: 20px;
        width: 100%;
        .zc-count {
            position: absolute;
            right: 15px;
            top: 4px;
            font-size: 12px;
            color: #393939;
            span {
                color: #EC5835;
            }
        }
    }
}
</style>
