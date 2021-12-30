<template>
		<section class="data_section" ref="data_section"> 
            <!-- 各个选择项 -->
			<el-row :gutter="10" class="row_list">
					<el-col :span="5">
						<div class="row_left row_base">
							Tribe
							<el-select v-model="value" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="5">
						<div class="row_left row_base">
							Liner
							<el-select v-model="value" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="5">
						<div class="row_left row_base">
							SG
							<el-select v-model="value" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
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
							<el-select v-model="value" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
					<el-col :span="5">
						<div class="row_left row_base">FeatureID
							<el-select v-model="value" placeholder="请选择" multiple  @change="changeValue()" @remove-tag="deleteValue">
								<el-option
								v-for="item in options"
								:key="item.value"
								:label="item.label"
								:value="item.value">
								</el-option>
							</el-select>
						</div>
					</el-col>
			</el-row>

			<!-- 更新+图表 --> -->
		    <el-row :gutter="10" class="row_list order_list">
				<el-col :span="24">
					<bar-chart type="barChart"></bar-chart>
				</el-col>
				<!-- <el-col :span="12">
				    <pie-chart type="ordertype"></pie-chart>
				</el-col> -->
			</el-row>
            <!-- <el-row :gutter="10" class="row_list order_list">
				<el-col :span="12">
					<line-chart></line-chart>
				</el-col>
			   	<el-col :span="12">
					<radar-chart></radar-chart>
				</el-col>
			</el-row> -->
			
			<!--表格-->
			<!-- <el-row :gutter="10" class="row_list order_list">
				<el-col :span="24">
					<user-list></user-list>
				</el-col>
			</el-row> -->

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
// import salesTable from "@/page/index/components/salesTable"; // 销售数据表格
// import commentList from "@/page/index/components/commentList"; // 用户评论列表
// import cardList from "@/page/index/components/cardList"; // card列表
// import logList from "@/page/index/components/logList"; // 日志列表
import barChart from "cps/echarts/barChart"; // 用户投资类型 柱状图
import pieChart from "cps/echarts/pieChart"; // 用户投资类型 饼状图
import radarChart from "cps/echarts/radarChart"; // 用户投资类型 雷达图
import lineChart from "cps/echarts/lineChart"; // 用户投资类型 折线图
// import { github } from "@/utils/env";

export default {
  data() {
    return {
      github: github,
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
        value: ''
    };
  },
  components: {
    barChart,
    pieChart,
    radarChart,
    lineChart,
  },
  created() {},
  mounted() {},
  methods: {},
};
</script>

<style lang="less" scoped>
.data_section {
  margin: 20px;
  border-radius: 2px;
  .row_list {
    margin-bottom: 20px;
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
      height: 450px;
      background: #fff !important;
      border-radius: 6px;
      box-sizing: border-box;
      padding: 10px;
      padding-top: 40px;
      overflow: hidden;
    }
    .orderbarArea {
      height: 500px;
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
