---
title: el-table
tags: 新建,模板,小书匠
category: /小书匠/日记/2022-12
emoji: "☺"
grammar_cjkRuby: true
---

官方写法

``` javascript
  <template>
    <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
    </el-table>
  </template>

  <script>
    export default {
      data() {
        return {
          tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }]
        }
      }
    }
  </script>
```
项目中实际用法：

``` javascript
<el-table
  :data="tableData"
  height="450"   //作用：固定表头
  :default-sort="{ prop: 'num', order: 'descending' }" //默认某列排序，倒序
>
  <el-table-column type="index" width="50" label="序号">
  </el-table-column>
  <template v-for="{ prop, label } in colConfigs">
	<el-table-column
	  v-if="prop === 'resourceType'"
	  :key="prop"
	  :prop="prop"
	  :label="label"
	  sortable
	  show-overflow-tooltip
	>
	  <template slot-scope="scope">
		<span v-if="scope.row.resourceType === 1">功能服务</span>
		<span v-else-if="scope.row.resourceType === 0">地图服务</span>
	  </template>
	</el-table-column>
	<el-table-column
	  v-else
	  show-overflow-tooltip
	  :key="prop"
	  :prop="prop"
	  :label="label"
	  sortable
	>
	</el-table-column>
  </template>
</el-table>
```