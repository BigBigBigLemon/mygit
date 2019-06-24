<template>
  <div class="page-register">
    <el-table
      :data="tableData"
      row-key="id"
      border
      default-expand-all
      highlight-current-row
      @current-change="handleCurrentChange"
      :tree-props="{children: 'children', hasChildren: 'hasChildren'}"
    >
      <el-table-column prop="date" label="日期" width="150"></el-table-column>
      <el-table-column label="配送信息">
        <el-table-column prop="name" label="姓名"></el-table-column>
        <el-table-column label="地址">
          <el-table-column prop="province" label="省份">
            <template slot-scope="scope">
              <el-input v-if="scope.row._edit" v-model="scope.row.province"></el-input>
              <span v-else class="cellInfo">{{scope.row.province}}</span>
            </template>
          </el-table-column>
          <el-table-column prop="city" label="市区">
            <template slot-scope="scope">
              <el-input v-if="scope.row._edit" v-model="scope.row.city"></el-input>
              <span v-else class="cellInfo">{{scope.row.city}}</span>
            </template>
          </el-table-column>
          <el-table-column prop="address" label="地址">
            <template slot-scope="scope">
              <el-input v-if="scope.row._edit" v-model="scope.row.address"></el-input>
              <span v-else class="cellInfo">{{scope.row.address}}</span>
            </template>
          </el-table-column>
          <el-table-column prop="zip" label="邮编">
            <template slot-scope="scope">
              <el-input-number v-if="scope.row._edit" v-model="scope.row.zip" controls-position="right" ></el-input-number>
              <span v-else class="cellInfo">{{scope.row.address}}</span>
            </template>
          </el-table-column>
        </el-table-column>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tableData: [
        {
          id: 1,
          date: '2016-05-02',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        },
        {
          id: 2,
          date: '2016-05-04',
          name: '王大毛',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        },
        {
          id: 3,
          date: '2016-05-01',
          name: '奥特曼',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333,
          children: [
            {
              id: 31,
              date: '2016-05-01',
              name: '皮卡丘',
              province: '上海',
              city: '普陀区',
              address: '上海市普陀区金沙江路 1518 弄',
              zip: 200333
            },
            {
              id: 32,
              date: '2016-05-01',
              name: '雷佳音',
              province: '上海',
              city: '普陀区',
              address: '上海市普陀区金沙江路 1518 弄',
              zip: 200333
            }
          ]
        },
        {
          id: 4,
          date: '2016-05-03',
          name: '孙红雷',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }
      ],
      // data_type：列的类型 ==> img图片，text字符串，numeric数值，checkbox单选框，date日期选择器，dialog模态框按钮，txtbtn文字按钮，button按钮
      title: [
        { data_type: '', key: 'org_name', title: '' },
        {
          data_type: 'text',
          key: 'date',
          title: '日期'
        },
        {
          title: '配送信息',
          children: [
            {
              data_type: 'text',
              key: 'name',
              title: '姓名'
            },
            {
              title: '地址',
              children: [
                {
                  data_type: 'text',
                  key: 'province',
                  title: '省份'
                },
                {
                  data_type: 'text',
                  key: 'city',
                  title: '市区'
                },
                {
                  data_type: 'text',
                  key: 'address',
                  title: '地址'
                },
                {
                  data_type: 'text',
                  key: 'zip',
                  title: '邮编'
                }
              ]
            }
          ]
        }
      ]
    }
  },
  layout: 'blank',
  methods: {
    handleCurrentChange (currentRow, oldCurrentRow) {
      this.$set(currentRow, '_edit', true)
      if (oldCurrentRow) this.$set(oldCurrentRow, '_edit', false)
      console.log(currentRow, oldCurrentRow)
    }
  }
}
</script>

<style lang="scss">
</style>
