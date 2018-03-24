<template>
  <div class="pos">
     <el-row>
         <el-col :span='7' class="pos-order" id="order-list">
             <el-tabs class="" @tab-click="tabclick">
                 <el-tab-pane label='点餐'>
                     <el-table :data="tableDate" border style="width:100%">
                         <el-table-column prop="goodsName" label="商品名称"></el-table-column>
                         <el-table-column prop="count" label="数量" width="50"></el-table-column>
                         <el-table-column prop="price" label="金额" width="70"></el-table-column>
                         <el-table-column label="操作" width="100" fixed="right">
                             <template slot-scope="scope">
                                 <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                                 <el-button type="text" size="small" @click="addOrderList(scope.row)">添加</el-button>
                             </template>
                         </el-table-column>
                     </el-table>
                     <div class="totalDiv">
                         <small>总数：</small>
                         <strong>{{totalCount}}</strong>
                         <small>总价：</small>
                         <strong>{{totalMoney}}</strong>元
                     </div>
                     <div class="divBtn">
                         <el-button type="warning" @click="setGuadan()">挂单</el-button>
                         <el-button type="danger" @click="delAll()">删除</el-button>
                         <el-button type="success" @click="chackout()">结账</el-button>
                     </div>
                 </el-tab-pane>
                 <el-tab-pane label='挂单' >
                     <el-table :data="guadanData" border style="width:100%">
                         <el-table-column prop="goodsName" label="商品名称"></el-table-column>
                         <el-table-column prop="count" label="数量" width="50"></el-table-column>
                         <el-table-column prop="price" label="金额" width="70"></el-table-column>
                         <el-table-column label="操作" width="100" fixed="right">
                             <template slot-scope="scope">
                                 <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                                 <el-button type="text" size="small" @click="addOrderList(scope.row)">添加</el-button>
                             </template>
                         </el-table-column>
                     </el-table>
                     <div class="totalDiv">
                         <small>总数：</small>
                         <strong>{{guadanCount}}</strong>
                         <small>总价：</small>
                         <strong>{{guadanMoney}}</strong>元
                     </div>
                     <div class="divBtn">
                         <el-button type="success" @click="chackout()">结账</el-button>
                     </div>
                 </el-tab-pane>
                 <el-tab-pane label='外卖'>
                     <el-table :data="tableDate" border style="width:100%">
                         <el-table-column prop="goodsName" label="商品名称"></el-table-column>
                         <el-table-column prop="count" label="数量" width="50"></el-table-column>
                         <el-table-column prop="price" label="金额" width="70"></el-table-column>
                         <el-table-column label="操作" width="100" fixed="right">
                             <template slot-scope="scope">
                                 <el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
                                 <el-button type="text" size="small" @click="addOrderList(scope.row)">添加</el-button>
                             </template>
                         </el-table-column>
                     </el-table>
                     <div class="totalDiv">
                         <small>总数：</small>
                         <strong>{{totalCount}}</strong>
                         <small>总价：</small>
                         <strong>{{totalMoney}}</strong>元
                     </div>
                     <div class="divBtn">
                         <el-button type="warning" >接单</el-button>
                         <el-button type="danger" >拒绝</el-button>
                         <el-button type="success" @click="chackout()">结账</el-button>
                     </div>
                 </el-tab-pane>
             </el-tabs>
         </el-col>
         <el-col :span="17">
            <div class="often-goods">
                <div class="title">常用商品</div>
                <div class="often-goods-list">
                    <ul>
                        <li v-for="goods in oftenGoods" @click="addOrderList(goods)">
                            <span>{{goods.goodsName}}</span>
                            <span class="o-price">￥{{goods.price}}元</span>
                        </li>
                    </ul>
                </div>
            </div>

            <div class="goods-type">
                <el-tabs>
                    <el-tab-pane label="汉堡">
                        <ul class="cookList">
                            <li v-for="foods in type0Goods" @click="addOrderList(foods)">
                                <span class="foodImg"><img :src="foods.goodsImg" width="100%"></span>
                                <span class="foodName">{{foods.goodsName}}</span>
                                <span class="foodPrice">￥{{foods.price}}元</span>

                            </li>
                        </ul>
                    </el-tab-pane>
                    <el-tab-pane label="小食">
                        <ul class="cookList">
                            <li v-for="foods in type1Goods" @click="addOrderList(foods)">
                                <span class="foodImg"><img :src="foods.goodsImg" width="100%"></span>
                                <span class="foodName">{{foods.goodsName}}</span>
                                <span class="foodPrice">￥{{foods.price}}元</span>

                            </li>
                        </ul>
                    </el-tab-pane>
                    <el-tab-pane label="饮料">
                        <ul class="cookList">
                            <li v-for="foods in type2Goods" @click="addOrderList(foods)">
                                <span class="foodImg"><img :src="foods.goodsImg" width="100%"></span>
                                <span class="foodName">{{foods.goodsName}}</span>
                                <span class="foodPrice">￥{{foods.price}}元</span>

                            </li>
                        </ul>
                    </el-tab-pane>
                    <el-tab-pane label="套餐">
                        <ul class="cookList">
                            <li v-for="foods in type3Goods" @click="addOrderList(goods)">
                                <span class="foodImg"><img :src="foods.goodsImg" width="100%"></span>
                                <span class="foodName">{{foods.goodsName}}</span>
                                <span class="foodPrice">￥{{foods.price}}元</span>

                            </li>
                        </ul>
                    </el-tab-pane>
                </el-tabs>
            </div>
         </el-col>
         
     </el-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Pos",
  data() {
    return {
      oftenURL: "http://jspang.com/DemoApi/oftenGoods.php",
      typeURL: "http://jspang.com/DemoApi/typeGoods.php",
      postURL: "", //结账服务器地址
      tableDate: [],
      oftenGoods: [],
      type0Goods: [],
      type1Goods: [],
      type2Goods: [],
      type3Goods: [],
      totalCount: 0,
      totalMoney: 0,
      guadanData: [],
      guadanCount: 0,
      guadanMoney: 0
    };
  },
  created: function() {//组件创建完成
    axios
      .get(this.oftenURL)
      .then(response => {
        //   console.log(response)
        this.oftenGoods = response.data;
      })
      .catch(error => {
        this.$massage.error("网络问题无法访问");
        alert("网络问题，无法访问");
      });
    axios
      .get(this.typeURL)
      .then(response => {
        //   console.log(response)
        this.type0Goods = response.data[0];
        this.type1Goods = response.data[1];
        this.type2Goods = response.data[2];
        this.type3Goods = response.data[3];
      })
      .catch(error => {
        alert("网络问题，无法访问");
      });
  },
  mounted: function() {//组件挂载完成
    //获取浏览器高
    var orderHeight = document.body.clientHeight;
    //赋值给容器高
    document.getElementById("order-list").style.height = orderHeight + "px";
  },
  methods: {
    addOrderList(goods) {
      //清楚总数和总价
      this.totalCount = 0;
      this.totalMoney = 0;
      let isHave = false; //标记
      //判断商品是否已经存在于订单列表
      for (let i = 0; i < this.tableDate.length; i++) {
        if (this.tableDate[i].goodsId == goods.goodsId) {
          isHave = true;
        }
      }
      //根据标记判断订单列表是否已有次商品
      if (isHave) {
        //存在添加数量
        let arr = this.tableDate.filter(o => o.goodsId == goods.goodsId);
        arr[0].count++;
      } else {
        //不存在推入数组
        let newGoods = {
          goodsId: goods.goodsId,
          goodsName: goods.goodsName,
          price: goods.price,
          count: 1
        };
        this.tableDate.push(newGoods);
      }
      this.getAlltableDate();
    },
    //计算总数总价格方法
    getAlltableDate() {
      this.totalCount = 0;
      this.totalMoney = 0;
      if (this.tableDate) {
        //计算总数总价
        this.tableDate.forEach(element => {
          this.totalCount += element.count;
          this.totalMoney = this.totalMoney + element.price * element.count;
        });
      }
    },
    //结账
    chackout() {
      if (this.totalCount != 0) {
          /** 此处应当发送到sever端 **/
        // axios
        //   .post(this.postURL, this.tableDate, {
        //     headers: {
        //       "Content-Type": "application/x-www-form-urlencoded"
        //     }
        //   })
        //   .then(function(response) {
        //     //console.log(response);

        //   })
        //   .catch(function(error) {
        //     // console.log(error);
        //   });
        /** 此处应当放到then方法中 **/
        this.tableDate = [];
        this.totalMoney = 0;
        this.totalCount = 0;
        this.$message({
          message: "结账成功！",
          type: "success"
        });
        /** **/
      } else {
        this.$message.error("请选择商品进行结账！");
      }
    },
    //挂单按钮保存到sessionStorage
    /** 其实此处也应当发送到sever端，只是用session做演示 **/
    setGuadan() {
      if (this.totalCount != 0) {
        this.tableDate.forEach(itme => {
          sessionStorage.setItem(itme.goodsId, JSON.stringify(itme));
          //   console.log(JSON.stringify(itme));
        });
        this.$message({//elementUI成功提示框
          message: "挂单存储成功！",
          type: "success"
        });
      } else {
        this.$message.error("请选择商品进行挂单！");//错误提示框
      }
    },
    //点击TAB事件
    tabclick(tab, event) {
      // console.log(event)
      let guadanId = event.target.getAttribute("id");
      //判断点击的是挂单标签
      if (guadanId == "tab-1") {
        this.guadanCount = 0;
        this.guadanMoney = 0;
        this.guadanData = [];
         // 取sessionStorage挂单信息
        let storage = window.sessionStorage;
        for (let k in storage) {
          //   console.log(storage[k]);
          if (storage[k] != "WARN") {
            this.guadanData.push(JSON.parse(storage[k]));
          }
        }
        if (this.guadanData) {//判断挂单数据是否存在
          //计算总数总价
          this.guadanData.forEach(element => {
            this.guadanCount += element.count;
            this.guadanMoney = this.guadanMoney + element.price * element.count;
          });
        }
      }else if(guadanId == "tab-2"){//判断点击的是外卖标签
      /** 此处应当是服务器端的推送消息 **/
        this.$message.error('目前没有外卖信息')
      }
    },
    //删除所有商品
    delAll() {
      this.tableDate = [];
      this.totalCount = 0;
      this.totalMoney = 0;
    },
    //单个商品删除
    delSingleGoods(goods) {
      this.tableDate = this.tableDate.filter(o => o.goodsId != goods.goodsId);
      this.getAlltableDate();
    }
  }
};
</script>

<style scoped>
.pos-order {
  background-color: #f9fafc;
  border-right: 1px solid;
  height: 100%;
}
.divBtn {
  text-align: center;
  margin-top: 10px;
}
.title {
  height: 20px;
  border-bottom: 1px solid #d3dce6;
  background-color: #f9fafc;
  padding: 10px;
  text-align: center;
}
.totalDiv {
  text-align: right;
  padding: 10px;
  background-color: #fff;
  border-bottom: 1px solid #d3dce6;
}
.totalDiv > strong:nth-child(2) {
  margin-right: 20px;
}
.often-goods-list ul li {
  list-style: none;
  float: left;
  border: 1px solid #e5e9f2;
  padding: 10px;
  margin: 5px;
  background-color: #fff;
  cursor: pointer;
}
.o-price {
  color: #58b7ff;
}
.goods-type {
  clear: both;
  /* padding-left: 5px; */
}
.cookList li {
  list-style: none;
  width: 23%;
  border: 1px solid #e5e9f2;
  height: auot;
  overflow: hidden;
  background-color: #fff;
  padding: 2px;
  float: left;
  margin: 2px;
  cursor: pointer;
}
.cookList li span {
  display: block;
  float: left;
}
.foodImg {
  width: 40%;
}
.foodName {
  font-size: 16px;
  padding-left: 10px;
  color: brown;
}
.foodPrice {
  font-size: 14px;
  padding-left: 10px;
  padding-top: 10px;
  width: 40%;
}

.el-tabs--top .el-tabs__item.is-top:nth-child(2) {
  padding-left: 20px !important;
}
</style>


