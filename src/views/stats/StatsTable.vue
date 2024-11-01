<template>
  <div class="">
    <mo-table
      v-bind="$attrs"
      v-on="$listeners"
    >
      <el-table-column
        align="center"
        label="序号"
       
      >
        <template slot-scope="scope">
          {{ scope.$index + 1}}
        </template>
      </el-table-column>

      <el-table-column
        label="项目名"
        align="center"
  
      >
        <template slot-scope="scope">
          {{scope.row.site_name || '-'}}
        </template>
      </el-table-column>

      <el-table-column
        label="来源"
        align="center"
      >
        <template slot-scope="scope">
          {{scope.row.source || '-'}}
        </template>
      </el-table-column>

      <el-table-column
        label="Spider"
        align="center"
      
      >
        <template slot-scope="scope">

          {{scope.row.name}}

        </template>
      </el-table-column>

      <el-table-column
        label="本次所有数量"
        align="center"
      
      >
        <template slot-scope="scope">
          {{scope.row.this_time_all_request}}
        </template>
      </el-table-column>

      <el-table-column
        label="本次成功数量"
        align="center"
   
      >
        <template slot-scope="scope">
          {{scope.row.this_time_success_request}}
        </template>
      </el-table-column>

      <el-table-column
        label="本次失败数量"
        align="center"
      >
        <template slot-scope="scope">
          <span style="color: red;">{{ scope.row.this_time_fail_request }}</span>
        </template>
      </el-table-column>


      <el-table-column
        label="今日所有数量"
        align="center"
      
      >
        <template slot-scope="scope">
          {{scope.row.today_all_request}}
        </template>
      </el-table-column>

      <el-table-column
        label="今日成功数量"
        align="center"
  
      >
        <template slot-scope="scope">
          {{scope.row.today_success_request}}
        </template>
      </el-table-column>

      <el-table-column
        label="今日失败数量"
        align="center"
      >
        <template slot-scope="scope">
          <span style="color: red;"> {{scope.row.today_fail_request}}</span>
        </template>
      </el-table-column>

      <el-table-column
        label="持续时间(s)"
        align="center"
        prop="duration"
        sortable="custom"
      >
        <template slot-scope="scope">
          <mo-text :text="scope.row.run_time"></mo-text>
        </template>
      </el-table-column>

      <el-table-column
        label="最后运行时间"
        align="center"

      >
        <template slot-scope="scope">

          {{scope.row.last_time}}

        </template>
      </el-table-column>

      <el-table-column
        label="运行次数"
        align="center"
        width="60"
      >
        <template slot-scope="scope">

          {{scope.row.crawl_count}}

        </template>
      </el-table-column>

    </mo-table>
  </div>
</template>

<script>
export default {
  name: '',
};
</script>

<style lang="scss" scoped>
</style>