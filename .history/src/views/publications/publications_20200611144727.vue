<template>
  <div>
    <div class="heade fl j-between">
      <div></div>
      <div>
        <el-row>
          <el-button type="danger">查看</el-button>
          <el-button type="primary">发布</el-button>
        </el-row>
      </div>
    </div>
    <div>
      <div class="layout fl">
        <div class="mg-t10 "><img src="../../assets/必填.png" alt class="tag" />文章标题:</div>
        <div><el-input class="el-ipt" v-model="value" size="small"  clearable ></el-input></div>
      </div>
      <div class="layout fl">
        <div class="mg-t10 "><img src="../../assets/必填.png" alt class="tag" />文章摘要:</div>
        <div><el-input class="el-ipt" v-model="value" size="small"  clearable ></el-input></div>
      </div>
    </div>
    <div class="fl j-between fz12">
      <div class="layout fl">
        <div class="writer"><img src="../../assets/必填.png" alt class="tag" />作者：</div>
        <div><el-input v-model="value" size="small" class="el-input" clearable ></el-input></div>
      </div>
      <div class="layout">
        <img src="../../assets/必填.png" alt class="tag" />类目：
        <el-select v-model="value1" size="small" clearable placeholder="请选择">
          <el-option
            v-for="item in options1"
            :key="item.value1"
            :label1="item.label1"
            :value1="item.value1"
          ></el-option>
        </el-select>
      </div>
      <div class="layout">
        <img src="../../assets/必填.png" alt class="tag" />来源：
        <el-select v-model="value2" size="small" clearable placeholder="请选择">
          <el-option
            v-for="item in options2"
            :key="item.value2"
            :label2="item.label2"
            :value2="item.value2"
          ></el-option>
        </el-select>
      </div>
      <div class="layout">
        <img src="../../assets/必填.png" alt class="tag" />重要性：
        <el-select v-model="value3" size="small" clearable placeholder="请选择">
          <el-option
            v-for="item in options3"
            :key="item.value3"
            :label3="item.label3"
            :value3="item.value3"
          ></el-option>
        </el-select>
      </div>
      <div class="layout">
        
        <div class="block">
        <img src="../../assets/必填.png" alt class="tag" />发布时间：
          <el-date-picker
          size="small"
            v-model="valueitem2"
            align="right"
            type="date"
            placeholder="选择时间日期"
            :picker-options="pickerOptions"
          ></el-date-picker>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "",
  props: {},
  components: {},
  data() {
    return {
      options1: [
        {
          label1: "Vue"
        },
        {
          label1: "React"
        },
        {
          label1: "Node.js"
        },
        {
          label1: "性能优化"
        },
        {
          label1: "JavaScript"
        },
        {
          label1: "小程序"
        },
        {
          label1: "工具类"
        },
        {
          label1: "其它"
        }
      ],
      value1: "",
    //  上面是类目使用的数组和定义的value
      options2: [
 
        {
          label: "原创"
        },
        {
          label: "转载"
        },
        {
          label: "他人合作"
        }
        ],
         value2: "",
        //  上面是来源使用的数组和value2
      options3: [
        {
          label: "1♥"
        },
        {
          label: "2♥"
        },
        {
          label: "3♥"
        }, 
        {
          label: "4♥"
        }, 
        {
          label: "5♥"
        }, 
        ],
      value3: "",
      // 这里是重要性使用的数组和value3 
      pickerOptions: {
          disabledDate(time) {
            return time.getTime() > Date.now();
          },
          shortcuts: [{
            text: '今天',
            onClick(picker) {
              picker.$emit('pick', new Date());
            }
          }, {
            text: '昨天',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit('pick', date);
            }
          }, {
            text: '一周前',
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', date);
            }
          }]
        },
        valueitem1: '',
        valueitem2: '',
    };
  },
  methods: {},
  mounted() {},
  watch: {},
  computed: {}
};
</script>
  
<style scoped lang='scss'>
.heade {
  margin: 35px 0 20px 20px;
  width: 97%;
  height: 50px;
  background: #59a586;
}
.el-button {
  margin: 5px 10px 0 0;
}
.writer {
  margin-top: 5px;
}
.tag {
  width: 16px;
}
.el-input {
  width: 150px;
}
.el-ipt {
  width: 1200px;

}
.el-select {
width: 150px;
}

</style>