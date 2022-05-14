<template>
	<div class="hello">
		<el-row class="m-t-20">
			<el-col :span="16" :offset="4">
				<el-input v-model="buy" placeholder="进价"></el-input>
			</el-col>
		</el-row>

		<el-row class="m-t-20">
			<el-col :span="16" :offset="4">
				<el-input v-model="shipping" placeholder="运费"></el-input>
			</el-col>
		</el-row>

		<el-button type="primary" class="m-t-20" @click="calc()">计算</el-button>
		<el-button type="danger" class="m-t-20" @click="clear()">清除</el-button>

		<el-table :data="tableData" height="550" border style="width: 100%">
			<el-table-column prop="sell" label="售价">
			</el-table-column>
			<el-table-column prop="earn" label="利润">
			</el-table-column>
		</el-table>
	</div>
</template>

<script>
	export default {
		name: 'HelloWorld',
		data() {
			return {
				buy: '',
				shipping: '',
				tableData: []
			}
		},
		methods: {
			calc() {
				if (this.buy && this.shipping) {
					this.tableData = [];
					var self = this;
					for (var i = 700; i <= 2000; i += 50) {
						var obj = new Object();
						obj.sell = i;
						obj.earn = i * 0.8 - self.buy - self.shipping;
						self.tableData.push(obj);
					}
				} else {
					this.$message({
						message: '请输入完整信息',
						type: 'warning'
					});
				}
			},
			
			clear () {
				this.buy = '';
				this.shipping = '';
				this.tableData = '';
			}
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.m-t-20 {
		margin-bottom: 20px;
	}
</style>
