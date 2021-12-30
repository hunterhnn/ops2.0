<template>
    <div class="fillcontain">
        <div class="contain">
          <div class="table_container">
            <el-table
                 v-loading="loading"
                 :data="tableData"
                 highlight-current-row
                 header-cell-class-name="table-header-class"
                 style="width:100%"
                 :row-style="{height: '80px'}">

                <el-table-column type="expand" class="text">
                    <template slot-scope="props">
                        <el-form label-position="left" inline class="demo-table-expand">
                        <el-form-item label="商品名称">
                            <span>{{ props.row.name }}</span>
                        </el-form-item>
                        <el-form-item label="所属店铺">
                            <span>{{ props.row.shop }}</span>
                        </el-form-item>
                        <el-form-item label="商品 ID">
                            <span>{{ props.row.id }}</span>
                        </el-form-item>
                        <el-form-item label="店铺 ID">
                            <span>{{ props.row.shopId }}</span>
                        </el-form-item>
                        <el-form-item label="商品分类">
                            <span>{{ props.row.category }}</span>
                        </el-form-item>
                        <el-form-item label="店铺地址">
                            <span>{{ props.row.address }}</span>
                        </el-form-item>
                        <el-form-item label="商品描述">
                            <span>{{ props.row.desc }}</span>
                        </el-form-item>
                        </el-form>
                    </template>
                </el-table-column>

                <el-table-column
                   label="FeatureID"
                   property="id"
                   align='center'>
                   <template slot-scope="scope">
                       <span>{{scope.$index+(paginations.pageIndex - 1) * paginations.pageSize + 1}} </span>
                    </template>
                </el-table-column>
                 <el-table-column
                   property="food_name"
                   label="Effort Spent"
                   width="200"
                   align='center'>
                   <el-progress :show-text="false" :stroke-width="10" :percentage="100" status="success"></el-progress>

                    <el-progress :text-inside="true" :stroke-width="15" :percentage="80" ></el-progress>
                </el-table-column>
                <el-table-column
                   property="email"
                   label="Status"
                   width="150"
                   align='center'>
                   <!-- <el-progress type="circle" :percentage="100" status="success" width="40" stroke-width="2"></el-progress> -->
                <!-- <el-progress type="dashboard" :percentage="percentage" :color="colors" width="80"></el-progress> -->
                {{hhh}}
                </el-table-column>
                <el-table-column
                   property="address"
                   label="DoD Score"
                   width="650"
                   align='center'>
                   <el-steps :space="120" :active="1" finish-status="success" align-center="true">
                        <el-popover
                            ref="popover1"
                            title="标题"
                            width="200"
                            trigger="hover"
                            close-delay=0
                            content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
                        </el-popover>
                        <el-popover
                            ref="popover2"
                            title="标题"
                            width="200"
                            trigger="hover"
                            close-delay=0
                            content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
                        </el-popover>
                        <el-popover
                            ref="popover3"
                            title="标题"
                            width="200"
                            trigger="hover"
                            close-delay=0
                            content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
                        </el-popover>
                        <el-step v-popover:popover1 title="FTS"></el-step>
                        <el-step v-popover:popover2 title="TP"></el-step>
                        <el-step v-popover:popover3 title="TC"></el-step>
                    </el-steps>
                </el-table-column>
                 <!-- <el-table-column
                   property="region"
                   label="FBExit Confirm"
                   width="150"
                   align='center'>
                   <el-switch
                    v-model="value1"
                    active-color="#13ce66"
                    active-text=""
                    inactive-text="">
                   </el-switch>
                </el-table-column>  -->
                  <!-- <el-table-column
                   property="DoD Compliance Pipeline"
                   label="网络"
                   width="80"
                   align='center'>
                </el-table-column>  -->
                 <!-- <el-table-column
                   property="ip"
                   label="IP地址"
                   width="180"
                   align='center'>
                </el-table-column>
                <el-table-column
                   property="createTime"
                   label="注册时间"
                   width="180"
                   align='center'>
                </el-table-column>
                <el-table-column
                   property="updateTime"
                   label="登录时间"
                   width="180"
                   align='center'>
                </el-table-column> -->
            </el-table>
           <el-row>
                <el-col :span="24">
                    <div class="pagination">
                        <el-pagination
                            v-if='paginations.total > 0'
                            :page-sizes="paginations.pageSizes"
                            :page-size="paginations.pageSize"
                            :layout="paginations.layout"
                            :total="paginations.total"
                            :current-page='paginations.pageIndex'
                            @current-change='handleCurrentChange'
                            @size-change='handleSizeChange'>
                        </el-pagination>
                    </div>
                </el-col>
            </el-row>
          </div>
        </div>
    </div>
</template>

<script>
    import { getUserList } from "@/api/user";
    export default {
        data(){
            return {
                tableData: [{
                    id: '1',
                    name: '好滋好味鸡蛋仔',
                    category: '江浙小吃、小吃零食',
                    desc: '荷兰优质淡奶，奶香浓而不腻',
                    address: '上海市普陀区真北路',
                    shop: '王小虎夫妻店',
                    shopId: '10333'
                    }, {
                    id: '2',
                    name: '好滋好味鸡蛋仔',
                    category: '江浙小吃、小吃零食',
                    desc: '荷兰优质淡奶，奶香浓而不腻',
                    address: '上海市普陀区真北路',
                    shop: '王小虎夫妻店',
                    shopId: '10333'
                    }, {
                    id: '3',
                    name: '好滋好味鸡蛋仔',
                    category: '江浙小吃、小吃零食',
                    desc: '荷兰优质淡奶，奶香浓而不腻',
                    address: '上海市普陀区真北路',
                    shop: '王小虎夫妻店',
                    shopId: '10333'
                    }, {
                    id: '4',
                    name: '好滋好味鸡蛋仔',
                    category: '江浙小吃、小吃零食',
                    desc: '荷兰优质淡奶，奶香浓而不腻',
                    address: '上海市普陀区真北路',
                    shop: '王小虎夫妻店',
                    shopId: '5'
                    }],
                loading:true,
              //需要给分页组件传的信息
                paginations: {
                    total: 0,        // 总数
                    pageIndex: 1,  // 当前位于哪页
                    pageSize: 10,   // 1页显示多少条
                    pageSizes: [5, 10],  //每页显示多少条
                    layout: "total, sizes, prev, pager, next, jumper"   // 翻页属性
                },
                percentage: 70,
                colors: [
                    {color: '#f56c6c', percentage: 20},
                    {color: '#e6a23c', percentage: 40},
                    {color: '#5cb87a', percentage: 60},
                    {color: '#1989fa', percentage: 80},
                    {color: '#6f7ad3', percentage: 100}
                ],
                value1: true,
                hhh:'Done'
            }
        },
        created(){
        },
        mounted(){
            this.getUserList();
        },
        methods: {
            // get_jsonLength(data){
            //     var length = 0;
            //     for(var i in data){
            //     length ++;
            //     }
            //     return length;
            // },
            // getData:function(){
            //     axios.get('').then(res=>{
            //         var limit=this.paginations.pageSize;
            //         var page=this.paginations.pageIndex;
            //         var userList=res.data.filter((item, index) => index < limit * page && index >= limit * (page - 1));
            //         var jLength=this.get_jsonLength(res.data);
            //         this.loading=false;
            //         this.paginations.total = jLength;
            //         this.tableData = userList;
            //     })
            //     .catch(error=>{
            //         alert(error);
            //     })
            // },
            getUserList(){
                let para = {
                    limit:this.paginations.pageSize,
                    page:this.paginations.pageIndex
                }
                getUserList(para).then(res => {
                    this.loading = false;
                    this.paginations.total = res.data.total;
                    this.tableData = res.data.userList;
                })
            },
            // 每页多少条切换
            handleSizeChange(pageSize) {
               this.paginations.pageSize = pageSize;
            //    this.getData();
                this.getUserList();
            },
            // 上下分页
            handleCurrentChange(page) {
               this.paginations.pageIndex = page;
            //    this.getData();
                this.getUserList();
            }
        },
    }
</script>

<style lang="less" scoped>
    .fillcontain{
        padding-bottom: 0;
    }
    .contain{
        background: #fff;
        // padding: 10px;
        margin-bottom: 20px;
        .text{
            font-size: 10%;
        }
    }
   .pagination{
    //    padding: 10px 20px;
       text-align: right;
   }
</style>



