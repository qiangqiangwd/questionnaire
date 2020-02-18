<template>
  <div>
    <div>
      <div class="operation">
        <div class="tit">我的调查表</div>
        <el-button size="small" @click="dialogVisible = true">设置城市</el-button>
        <el-button size="small">修改表单名称</el-button>
        <el-button size="small">设置调研目的</el-button>
        <el-button size="small">设置管辖小区</el-button>
        <el-button size="small">下载微信邀请码</el-button>
        <el-button size="small">下载小程序邀请码</el-button>
        <el-button size="small">查询统计结果</el-button>
        <el-button size="small">查询调研明细</el-button>
      </div>

      <!-- 弹出层 -->
      <el-dialog title="提示" :visible.sync="dialogVisible" width="30%" :before-close="handleClose">
        <div class="dialogContent">
          <div class="label">
            <div class="tit">标题：</div>
            <div class="rCnt">
              <el-input placeholder="请输入标题"></el-input>
            </div>
          </div>
          <div class="label">
            <div class="tit">所在城市：</div>
            <div class="rCnt">
              <el-select v-model="form.region" placeholder="省">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
              <el-select v-model="form.region" placeholder="城市">
                <el-option label="区域一" value="shanghai"></el-option>
                <el-option label="区域二" value="beijing"></el-option>
              </el-select>
            </div>
          </div>
        </div>
        <span slot="footer" class="dialog-footer">
          <el-button @click="dialogVisible = false">取 消</el-button>
          <el-button type="primary" @click="dialogVisible = false">保 存</el-button>
        </span>
      </el-dialog>

      <div class="title">社区"新冠"调查表</div>
      <div
        class="desc"
      >因目前新型冠状肺炎疫情严峻，为加强对社区的管理，秉持对个人、对家庭、对社会负责原则，请您花几分钟时间如实填写下面调查问卷。对您所填写的个人信息，我们会给予严格保密。</div>
      <el-form
        ref="form"
        :model="form"
        :rules="rules"
        label-width="260px"
        label-position="top"
        @submit.prevent="onSubmit"
        style="margin:20px;width:450px;"
      >
        <el-form-item label="1.您的姓名：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="2.您的性别：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="男"></el-radio>
            <el-radio label="女"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="3.您的年龄：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="4.您的身份证号：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="5.您的联系方式：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="6.您的现住地(小区楼栋单元房号)：" prop="region">
          <el-select v-model="form.region" placeholder="所在小区">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
          <el-input v-model="form.name" class="mt20" placeholder="楼栋信息"></el-input>
        </el-form-item>
        <el-form-item label="7.您的所居住的房屋性质：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="自有住房"></el-radio>
            <el-radio label="租住房"></el-radio>
            <el-radio label="其他"></el-radio>
          </el-radio-group>
          <el-input v-model="form.name" class="mt20" placeholder="其他"></el-input>
        </el-form-item>
        <el-form-item label="8.您的家中常住人数：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="9.近期(1月8日)以来接触过从湖北、重庆等疫情高发地区来访人员：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="是"></el-radio>
            <el-radio label="否"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="10.近期(1月29日)以来接触过外市的来访人员：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="是"></el-radio>
            <el-radio label="否"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="11.1月8日后是否去过市外：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="是"></el-radio>
            <el-radio label="否"></el-radio>
          </el-radio-group>
        </el-form-item>
        <el-form-item label="12.若您去过市外：">
          <el-select v-model="form.region" placeholder="所到城市">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
          <el-input v-model="form.name" class="mt20" placeholder="往返时间"></el-input>
          <el-select v-model="form.region" class="mt20" placeholder="出行方式">
            <el-option label="私车" value="shanghai"></el-option>
            <el-option label="火车" value="beijing"></el-option>
            <el-option label="汽车" value="beijing"></el-option>
            <el-option label="飞机" value="beijing"></el-option>
            <el-option label="船舶" value="beijing"></el-option>
            <el-option label="公交" value="beijing"></el-option>
            <el-option label="地铁" value="beijing"></el-option>
          </el-select>
          <el-input v-model="form.name" class="mt20" placeholder="车牌或班次"></el-input>
        </el-form-item>
        <el-form-item label="13.您及家人目前的身体状况：" prop="resource">
          <el-radio-group v-model="form.resource">
            <el-radio label="身体健康无异常"></el-radio>
            <el-radio label="自我隔离观察中"></el-radio>
            <el-radio label="确诊患病"></el-radio>
            <el-radio label="其他"></el-radio>
          </el-radio-group>
          <el-input v-model="form.name" class="mt20" placeholder="其他"></el-input>
        </el-form-item>
        <el-form-item label="14.今日测量体温(℃)：" prop="name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="15.您是否有以下症状：" prop="type">
          <el-checkbox-group v-model="form.type">
            <el-checkbox label="发热(≥37.3℃)" name="type"></el-checkbox>
            <el-checkbox label="咳嗽" name="type"></el-checkbox>
            <el-checkbox label="嗓子疼(喉咙疼）" name="type"></el-checkbox>
            <el-checkbox label="肌肉疼和关节疼" name="type"></el-checkbox>
            <el-checkbox label="鼻塞" name="type"></el-checkbox>
            <el-checkbox label="头疼" name="type"></el-checkbox>
            <el-checkbox label="流鼻涕" name="type"></el-checkbox>
            <el-checkbox label="呼吸困难" name="type"></el-checkbox>
            <el-checkbox label="乏力" name="type"></el-checkbox>
            <el-checkbox label="无上述症状" name="type"></el-checkbox>
          </el-checkbox-group>
        </el-form-item>
        <el-form-item label="16.您的诊疗请况：">
          <el-select v-model="form.region" placeholder="诊疗时间">
            <el-option label="区域一" value="shanghai"></el-option>
            <el-option label="区域二" value="beijing"></el-option>
          </el-select>
          <el-input v-model="form.name" class="mt20" placeholder="诊疗机构"></el-input>
          <el-select v-model="form.region" class="mt20" placeholder="诊疗结果">
            <el-option label="确诊" value="shanghai"></el-option>
            <el-option label="留观" value="beijing"></el-option>
            <el-option label="疑似" value="beijing"></el-option>
            <el-option label="解除观察" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="17.您的返(赴)所在区后接触的人员信息：">
          <div class="flexLast">
            <div>
              <el-input v-model="form.name" placeholder="姓名"></el-input>
              <el-input v-model="form.name" class="mt20" placeholder="性别"></el-input>
              <el-input v-model="form.name" class="mt20" placeholder="年龄"></el-input>
              <el-input v-model="form.name" class="mt20" placeholder="现住地"></el-input>
              <el-input v-model="form.name" class="mt20" placeholder="电话"></el-input>
            </div>
            <div class="delBtn">删除</div>
          </div>
        </el-form-item>
        <!-- <el-form-item>
          <el-button type="primary">立即创建</el-button>
          <el-button @click.native.prevent>取消</el-button>
        </el-form-item>-->
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: ""
      },
      rules: {
        name: [{ required: true, message: " ", trigger: "blur" }],
        resource: [{ required: true, message: " ", trigger: "change" }],
        type: [{ required: true, message: " ", trigger: "change" }],
        region: [{ required: true, message: " ", trigger: "change" }]
      },

      // 弹框显示和隐藏
      dialogVisible: false
    };
  },
  methods: {
    handleClose(done) {
      this.$confirm("确认关闭？")
        .then(_ => {
          done();
        })
        .catch(_ => {});
    }
  }
};
</script>

<style scoped lang="scss">
.title {
  text-align: center;
  font-size: 22px;
  font-weight: 500;
  margin-top: 15px;
}
.mt20 {
  margin-top: 10px;
}
.dialogContent {
  .label {
    display: flex;
    align-items: center;
    .tit {
      width: 80px;
    }
    .rCnt {
    //   width: 60%;
    }
  }
}
.operation {
  padding: 15px 0;
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
  border-bottom: 1px solid #cccccc;

  .tit {
    font-size: 18px;
  }
  // button{
  // 	// margin-top: 10px;
  // }
}
.desc {
  margin: 20px;
  color: #333333;
}
.flexLast {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.delBtn {
  width: 100px;
  // height: 200px;
  border: 1px solid #cccccc;
  text-align: center;
  line-height: 100px;
  color: #666666;
  margin-left: 20px;
  border-radius: 3px;
  cursor: pointer;
}
</style>