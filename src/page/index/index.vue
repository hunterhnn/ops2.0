
<template>
		<section class="data_section" ref="data_section"> 
			<!-- 最上方卡片 -->
			<!-- <a :href="github" target="_blank"> -->
				<!-- <el-row :gutter="10" class="row_list">
					<el-col :span="8">
						<div class="row_left row_base">
							<el-col :span="12">
								<div class="pay saleBgcolor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.yearLoss') }}</p>
										<p class="number">68<span class="perTitle">({{ $t('index.tenMillion') }})</span></p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconfukuan" />
									</div>
								</div>
							</el-col>
							<el-col :span="12">
								<div class="pay taxBgcolor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.yearProfit') }}</p>
										<p class="number">120<span class="perTitle">(%)</span></p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconpay3" />
									</div>
								</div>
							</el-col>
						</div>
					</el-col>
					<el-col :span="16">
						<div class="row_right row_base">
							<el-col :span="6">
								<div class="extenedBgcolor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.potentialInvestor') }}</p>
										<p class="number">686<span class="perTitle">({{ $t('index.person') }})</span></p>
										<p class="cardText">Decreased by 10%</p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconpay2" />
									</div>
								</div>
							</el-col>
							<el-col :span="6">
								<div class="likeBgcolor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.intentionInvestor') }}</p>
										<p class="number">1276<span class="perTitle">({{ $t('index.person') }})</span></p>
										<p class="cardText">Decreased by 50%</p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconpay1" />
									</div>
								</div>
							</el-col>
							<el-col :span="6">
								<div class="linkBgColor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.waitExamineInvestor') }}</p>
										<p class="number">82367<span class="perTitle">({{ $t('index.person') }})</span></p>
										<p class="cardText">Decreased by 30%</p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconpay" />
									</div>
								</div>
							</el-col>
							<el-col :span="6">
								<div class="keleBgColor data_list rflex">
									<div class="leftItem cflex wflex">
										<p class="investor">{{ $t('index.examiningInvestor') }}</p>
										<p class="number">827373<span class="perTitle">({{ $t('index.person') }})</span></p>
										<p class="cardText">Decreased by 80%</p>
									</div>
									<div class="rightItem">
										<icon-svg icon-class="iconfufei0" />
									</div>
								</div>
							</el-col>
						</div>
					</el-col>
				</el-row> -->
			<!-- </a> -->
			<el-row  class="row_list">
				<el-form :inline="true">
					<el-col :span="4">
						<el-form-item label="SG" class="row_left row_base">
						<el-select
							v-model="selectData.com1"
							placeholder="请选择"
							clearable
							@change="change1"
						>
							<el-option
							v-for="x in optionData.com1"
							:key="x.value"
							:value="x.value"
							:label="x.name"
							></el-option>
						</el-select>
						</el-form-item>
					</el-col>
					<el-col :span="4">
						<el-form-item label="Team" class="row_left row_base">
						<el-select
							v-model="selectData.com2"
							placeholder="请选择"
							clearable
							@change="change2"
						>
							<el-option
							v-for="x in optionData.com2[selectData.com1]"
							:key="x.value"
							:value="x.value"
							:label="x.name"
							></el-option>
						</el-select>
						</el-form-item>
					</el-col>
					<el-col :span="4">
						<el-form-item label="FB" class="row_left row_base">
						<el-select v-model="selectData.com3" placeholder="请选择" clearable>
							<el-option
							v-for="x in optionData.com3[selectData.com2]"
							:key="x.value"
							:value="x.value"
							:label="x.name"
							></el-option>
						</el-select>
						</el-form-item>
					</el-col>

					<!-- <el-col :span="4">
						<el-form-item label="FB" class="row_left row_base">
						<el-select v-model="value4" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
							<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
							</el-option>
						</el-select>
						</el-form-item>
					</el-col> -->

					<el-col :span="4">
						<el-form-item label="FeatureID" class="row_left row_base">
						<el-select v-model="value5" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
							<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
							</el-option>
						</el-select>
						</el-form-item>
					</el-col>

					<el-col :span="4">
						<el-form-item label="DoD Items" class="row_left row_base">
						<el-select v-model="value6" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
							<el-option
								v-for="item in options6"
								:key="item.value"
								:label="item.label"
								:value="item.value">
							</el-option>
						</el-select>
						</el-form-item>
					</el-col>

					<el-col :span="4">
						<el-form-item label="DoD Status" class="row_left row_base">
						<el-select v-model="value7" placeholder="请选择3" multiple  @change="changeValue()" @remove-tag="deleteValue">
							<el-option
								v-for="item in options7"
								:key="item.value"
								:label="item.label"
								:value="item.value">
							</el-option>
						</el-select>
						</el-form-item>
					</el-col>
				</el-form>
			</el-row>
            <!-- 各个选择项 -->
			<!-- <el-row :gutter="10" class="row_list">
					<el-col :span="3">
						<div class="row_left row_base">
							Tribe
							<el-select v-model="value1" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options1"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="3">
						<div class="row_left row_base">
							Liner
							<el-select v-model="value2" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options2"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="3">
						<div class="row_left row_base">
							SG
							<el-select v-model="value3" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options3"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>

					<el-col :span="4">
						<div class="row_left row_base">FeatureID
							<el-select v-model="value4" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="4">
						<div class="row_left row_base">FB
							<el-select v-model="value5" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="4">
						<div class="row_left row_base">DoD Items:
							<el-select v-model="value6" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options6"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="3">
						<div class="row_left row_base">DoD Status:
							<el-select v-model="value7" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options7"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
			</el-row> -->

			<!-- 更新+图表 -->
			<!-- <el-row :gutter="10" class="row_list order_list">
				<el-col :span="7">
					<log-list></log-list>
				</el-col>
				<el-col :span="17">
					<bar-chart type="barChart"></bar-chart>
				</el-col>
			</el-row> -->
			
			<!--表格-->
			<el-row :gutter="10" class="row_list order_list">
				<el-col :span="24">
					<user-list></user-list>
				</el-col>
			</el-row>

			<!-- <el-row :gutter="10" class="row_list order_list">
				<el-col :span="7">
				    <pie-chart type="ordertype"></pie-chart>
				</el-col>
				<el-col :span="10">
					<line-chart></line-chart>
				</el-col>
			   	<el-col :span="7">
					<radar-chart></radar-chart>
				</el-col>
			</el-row> 
			<el-row :gutter="10" class="row_list">
				<el-col :span="11">
					<sales-table></sales-table>
				</el-col>
				<el-col :span="7">
					<comment-list></comment-list>
				</el-col>
				<el-col :span="6">
					<card-list></card-list>
				</el-col>
			</el-row> -->
		</section>

</template>

<script>
import echarts from "echarts";
import salesTable from "./components/salesTable"; // 销售数据表格
import commentList from "./components/commentList"; // 用户评论列表
import cardList from "./components/cardList"; // card列表
import logList from "./components/logList"; // 日志列表
import userList from ".././userList/userList.vue"
import barChart from "cps/echarts/barChart"; // 用户投资类型 柱状图
import pieChart from "cps/echarts/pieChart"; // 用户投资类型 饼状图
import radarChart from "cps/echarts/radarChart"; // 用户投资类型 雷达图
import lineChart from "cps/echarts/lineChart"; // 用户投资类型 折线图
import { github } from "@/utils/env";

export default {
  data() {
    return {
      github: github,
	  selectData: {
        com1: "",
        com2: "",
        com3: "",
      },
	  optionData: {
        com1: [
          { value: "A", name: "控件1A" },
          { value: "B", name: "控件1B" },
          { value: "C", name: "控件1C" },
        ],
        com2: {
          A: [
            { value: "A1", name: "控件2A1" },
            { value: "A2", name: "控件2A2" },
            { value: "A3", name: "控件2A3" },
          ],
          B: [
            { value: "B1", name: "控件2B1" },
            { value: "B2", name: "控件2B2" },
          ],
          C: [
            { value: "C1", name: "控件2C1" },
            { value: "C2", name: "控件2C2" },
          ],
        },
        com3: {
          A1: [
            { value: "A11", name: "控件3A11" },
            { value: "A12", name: "控件3A12" },
          ],
          A2: [
            { value: "A21", name: "控件3A21" },
            { value: "A22", name: "控件3A22" },
          ],
          A3: [
            { value: "A31", name: "控件3A31" },
            { value: "A32", name: "控件3A32" },
            { value: "A33", name: "控件3A33" },
          ],
          B1: [
            { value: "B11", name: "控件3B11" },
            { value: "B12", name: "控件3B12" },
          ],
          B2: [{ value: "B21", name: "控件3B21" }],
          C1: [{ value: "C11", name: "控件3C11" }],
          C2: [
            { value: "C21", name: "控件3C21" },
            { value: "C22", name: "控件3C22" },
            { value: "C23", name: "控件3C23" },
          ],
        },
      },
	   options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
	// 	options1: [{
    //       value: '选项1',
    //       label: 'MN RAN Pz 1 HAZ'
    //     }, {
    //       value: '选项2',
    //       label: 'MN RAN Pz 2 HAZ'
    //     }, {
    //       value: '选项3',
    //       label: 'MN RAN Pz 3 HAZ'
    //     }, {
    //       value: '选项4',
    //       label: 'MN RAN Pz 4 HAZ'
	// 	}],
	// 	options2: [{
    //       value: '选项1',
    //       label: 'MN RAN Pz 2 HAZ SG1'
    //     }, {
    //       value: '选项2',
    //       label: 'MN RAN Pz 2 HAZ SG2'
    //     }, {
    //       value: '选项3',
    //       label: 'MN RAN Pz 2 HAZ SG3'
    //     }, {
    //       value: '选项4',
    //       label: 'MN RAN Pz 2 HAZ SG5'
	// 	}],
		options6: [{
          value: '选项1',
          label: 'FTS'
        }, {
          value: '选项2',
          label: 'TC'
        }, {
          value: '选项3',
          label: 'TP'
        }, {
          value: '选项4',
          label: 'XXX'
		}],
		options7: [{
          value: '选项1',
          label: 'Done'
        }, {
          value: '选项2',
          label: 'Open'
		}],
		value1: [],
        value2: [],
		value3: [],
        value4: [],
		value5: [],
        value6: [],
		value7: []
    }
  },
  components: {
    salesTable,
    commentList,
    cardList,
    logList,
    barChart,
    pieChart,
    radarChart,
    lineChart,
    userList,
  },
  created() {},
  mounted() {},
  methods: {
	  change1: function (val) {
      if (val) {
        this.selectData.com2 = this.optionData.com2[val][0].value; //根据第一个控件所选项确定第二个控件下拉内容的对象数组，并使默认为第一个数组项
        this.change2(); //控件2手动改变时会自动触发该方法，但是被动改变时不会触发，所以手动加上去
      } else {
        this.selectData.com2 = ""; //若前一个控件清空则后一个控件所选内容也清空
        this.change2();
      }
    },
    change2: function () {
      var val = this.selectData.com2;
      if (val) {
        this.selectData.com3 = this.optionData.com3[val][0].value;
      } else {
        this.selectData.com3 = "";
      }
    },
  },
};
</script>

<style lang="less" scoped>
.data_section {
  margin: 20px;
  border-radius: 2px;
  .row_list {
    // margin-bottom: 20px;
    .row_base {
      padding: 10px;
      box-sizing: border-box;
      background: #fff;
      border-radius: 6px;
      height: 80px;
    }
  }
  .order_list {
    .orderArea {
      width: 100%;
      height: 300px;
      background: #fff !important;
      border-radius: 6px;
      box-sizing: border-box;
      padding: 10px;
      padding-top: 10px;
	//   padding-top: 40px;
      overflow: hidden;
    }
    .orderbarArea {
      height: 370px;
    }
  }
  .data_list {
    text-align: center;
    font-size: 14px;
    border-radius: 6px;
    padding: 10px;
    color: #fff;
    height: 80px;
    .leftItem {
      align-items: start;
      justify-content: space-between;
      text-align: left;
    }
    .rightItem {
      width: 62px;
      display: flex;
      align-items: center;
      justify-content: center;
      .svg-icon {
        font-size: 30px;
      }
    }
    .number {
      font-size: 22px;
      font-weight: bold;
      .perTitle {
        font-size: 13px;
        margin-left: 5px;
      }
    }
  }
  .pay {
    .leftItem {
      justify-content: space-around;
    }
  }
}
</style>
