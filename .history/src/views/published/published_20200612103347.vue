<template>
  <div class="layout">
    <div class>
      <div class="fl">
        <div>
          <el-table
            ref="singleTable"
            :data="Article.slice((currentPage-1)*sizeChange,currentPage*sizeChange)"
            highlight-current-row
            border
            style="width: 100%"
            :row-class-name="tableRowClassName"
          >
            >
            <el-table-column label="#" type="index" width="50"></el-table-column>
            <el-table-column property="title" label="标题" width="300"></el-table-column>
            <el-table-column property="author" label="作者" width="150"></el-table-column>
            <el-table-column
              property="category"
              :filters="[{ text: 'Javascript', value: 'Javascript' }, { text: 'Nodejs', value: 'Nodejs' }]"
              :filter-method="filterTag"
              filter-placement="bottom-end"
              label="类目"
              width="100"
            ></el-table-column>
            <el-table-column property="source" label="来源" width="100"></el-table-column>
            <el-table-column property="star" label="重要性" width="100"></el-table-column>
            <el-table-column property="date" label="发布时间" width="300"></el-table-column>
            <el-table-column label="操作" width="320" class="fl">
              <el-button type="primary" size="mini">编辑</el-button>
              <el-button type="danger" size="mini" @click="del">删除</el-button>
              <el-button type="success" size="mini">查看</el-button>
            </el-table-column>
          </el-table>

          <el-table-column prop="tag" label="标签" width="100">
            <template slot-scope="scope">
              <el-tag
                :type="scope.row.tag === 'vue' ? 'primary' : 'success'"
                disable-transitions
              >{{scope.row.tag}}</el-tag>
            </template>
          </el-table-column>
        </div>
      </div>
    </div>
    <!--分页-->
    <div class="block">
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage"
        :page-sizes="[10, 20, 30, 40]"
        :page-size="sizeChange"
        layout="total, sizes, prev, pager, next, jumper"
        :total="Article.length"
      ></el-pagination>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "",
  props: {},
  components: {},
  data() {
    return {
      Article: [],

      currentPage: 1,
      sizeChange: 10
    };
  },
  methods: {
    // - 获取所有文章: /article/allArticle (get请求)
    getallrticle() {
      axios
        .get("/api/article/allArticle")
        .then(res => {
          this.Article = res.data.data;
          console.log(this.Article);
        })
        .catch(err => {
          console.log(err);
        });
    },
    handleSizeChange(val) {
      //  获取当前一夜的条数
      this.sizeChange = val;
    },
    handleCurrentChange(val) {
      // 获取当前页
      this.currentPage = val;
    },
    // 删除功能
    del() {
      this.Article.filter(item => {});
    },
    // 给tabel文字添加样式
    filterTag(value, row) {
        return row.tag === value;
      },
      filterHandler(value, row, column) {
        const property = column['property'];
        return row[property] === value;
      },
      // 给行添加样式
      tableRowClassName({row, rowIndex}) {
        if (rowIndex === 1) {
          return 'warning-row';
        } else if (rowIndex === 3) {
          return 'success-row';
        }
  },
  mounted() {
    this.getallrticle();
  },
  watch: {},
  computed: {}

</script>

<style scoped lang='scss'>
.el-table {
  margin: 0 auto;
  text-align: center;
}
.el-table .warning-row {
  background: rgb(182, 142, 69);
}

.el-table .success-row {
  background: #61df1d;
}
</style>