<template>
  <div>
    <el-breadcrumb separator="/">
      <el-breadcrumb-item :to="{ path: '/users' }">用户列表</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/roles' }">角色列表</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/rights' }">权限列表</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/goods' }">商品列表</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/params' }">分类参数</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/categories' }">商品分类</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/orders' }">订单列表</el-breadcrumb-item>
      <el-breadcrumb-item :to="{ path: '/reports' }">数据报表</el-breadcrumb-item>
      <el-breadcrumb-item>首页</el-breadcrumb-item>
    </el-breadcrumb>
    <el-card>
      <el-tabs type="card">
        <el-tab-pane label="项目介绍">
          <el-divider content-position="center">2. x 和 Vue 使用 UI 项目的后台管理，axios 调用系统主要调用了 Echarts、vue-quill-editor 等</el-divider>
          <el-row :gutter="20">
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/dl.png" :preview-src-list="srcList" alt="登录界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/sy.png" :preview-src-list="srcList" alt="首页界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/lxzz.png" :preview-src-list="srcList" alt="联系作者界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/yhlb.png" :preview-src-list="srcList" alt="用户列表界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/jslb.png" :preview-src-list="srcList" alt="角色列表界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/qxlb.png" :preview-src-list="srcList" alt="权限列表界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/splb.png" :preview-src-list="srcList" alt="商品列表界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/splbadd.png" :preview-src-list="srcList" alt="商品列表添加列表"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/flcs.png" :preview-src-list="srcList" alt="分类参数界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/spfl.png" :preview-src-list="srcList" alt="商品分类"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/ddlb.png" :preview-src-list="srcList" alt="订单列表界面"></el-image></el-col>
            <el-col :span="6"><el-image src="http://shop.xiaoder.cn/img/sjbb.png" :preview-src-list="srcList" alt="数据报表界面"></el-image></el-col>
          </el-row>
        </el-tab-pane>
        <el-tab-pane label="api接口">
          <el-alert title="线上接口数据" type="success" description="请勿使用https协议访问在线接口，接口地址：http://xiaoder.cn:8888/api/private/v1/" :closable="false"> </el-alert>
          <el-collapse>
            <el-collapse-item title="API V1 接口说明">
              <div>接口基准地址：`http://127.0.0.1:8888/api/private/v1/`</div>
              <div>服务端已开启 CORS 跨域支持</div>
              <div>API V1 认证统一使用 Token 认证</div>
              <div>需要授权的 API ，必须在请求头中使用 `Authorization` 字段提供 `token` 令牌</div>
              <div>使用 HTTP Status Code 标识状态</div>
              <div>数据返回格式统一使用 JSON</div>
            </el-collapse-item>
            <el-collapse-item title="支持的请求方法">
              <div>GET（SELECT）：从服务器取出资源（一项或多项）。</div>
              <div>POST（CREATE）：在服务器新建一个资源。</div>
              <div>PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。</div>
              <div>PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。</div>
              <div>DELETE（DELETE）：从服务器删除资源。</div>
              <div>HEAD：获取资源的元数据。</div>
              <div>OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。</div>
            </el-collapse-item>
            <el-collapse-item title=" 通用返回状态说明">
              <el-table :data="tableDataA" style="width: 100%" :row-class-name="tableRowClassName" border>
                <el-table-column type="index"></el-table-column>
                <el-table-column prop="num" label="状态码" width="180"> </el-table-column>
                <el-table-column prop="test" label="含义" width="180"> </el-table-column>
                <el-table-column prop="text" label="说明"> </el-table-column>
              </el-table>
            </el-collapse-item>
          </el-collapse>
          <el-empty image="http://shop.xiaoder.cn/img/api.png" description="接口文档/数据库下载">
            <a href="http://shop.xiaoder.cn/img/vueShop-api.zip"><el-button type="primary">下载</el-button></a>
          </el-empty>
        </el-tab-pane>
        <el-tab-pane label="项目源码">
          <el-empty image="http://shop.xiaoder.cn/img/ym.png" description="源码下载">
            <a href="http://shop.xiaoder.cn/img/dist.zip"><el-button type="primary" class="xz">源码下载</el-button></a>
            <a href="http://shop.xiaoder.cn/img/azoom_xm.zip"><el-button type="primary" class="xz">开发版本下载</el-button></a>
          </el-empty>
        </el-tab-pane>
        <el-tab-pane label="项目优化">
          <el-table :data="tableDataB" style="width: 100%" :row-class-name="tableRowClassName" border>
            <el-table-column type="index"></el-table-column>
            <el-table-column prop="text" label="模块" width="180"> </el-table-column>
            <el-table-column prop="test" label="优化点" width="180"> </el-table-column>
            <el-table-column prop="doc" label="优化功能"> </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="bug区域">
          <el-table :data="tableDataC" stripe style="width: 100%" border>
            <el-table-column type="index"></el-table-column>
            <el-table-column prop="text" label="模块" width="180"> </el-table-column>
            <el-table-column prop="test" label="作用" width="180"> </el-table-column>
            <el-table-column prop="doc" label="解决方案"> </el-table-column>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="开发周期">
          <el-alert title="（2021.3.8-2021.3.24）" type="success" center show-icon :closable="false"> </el-alert>
          <!-- 日历 -->
          <el-calendar v-model="value"> </el-calendar>
        </el-tab-pane>
        <!-- 下面这个close可有可无 -->
        <el-tab-pane label="联系作者" @close="close">
          <el-descriptions class="margin-top" title="作者介绍" :column="3" :size="size" border>
            <!-- <template slot="extra">
              <el-button type="primary" size="small">小惊喜</el-button>
            </template> -->
            <el-descriptions-item>
              <template slot="label">
                <i class="el-icon-user"></i>
                用户名
              </template>
              小der
            </el-descriptions-item>
            <el-descriptions-item>
              <template slot="label">
                <i class="el-icon-chat-line-round"></i>
                邮箱
              </template>
              derpro@foxmail.com
            </el-descriptions-item>
            <el-descriptions-item>
              <template slot="label">
                <i class="el-icon-location-outline"></i>
                居住地
              </template>
              杭州
            </el-descriptions-item>
            <el-descriptions-item>
              <template slot="label">
                <i class="el-icon-tickets"></i>
                备注
              </template>
              <el-tag size="small">打工人</el-tag>
            </el-descriptions-item>
            <el-descriptions-item>
              <template slot="label">
                <i class="el-icon-office-building"></i>
                联系地址
              </template>
              中国（China）
            </el-descriptions-item>
          </el-descriptions>
          <div class="buttonAlas"><el-button type="primary" round @click="dj" class="buttonClass" disabled>联系作者(跨域版本测试中，下面为内嵌写法。)</el-button></div>
          <div class="iframe">
            <iframe src="http://shop.xiaoder.cn/img/" frameborder="0" scrolling="no" width="350px" height="350px"></iframe>
          </div>
        </el-tab-pane>
      </el-tabs>
    </el-card>
    <el-dialog title="联系作者" :visible.sync="formIf" width="50%" @close="fsClose" center>
            <el-alert title="以下是调用公众号（方糖）的接口请勿反复点击" type="info" center show-icon :closable="false"> </el-alert>
            <el-form :model="ruleForm" :rules="fsRules" ref="fsRuleForm" label-width="80px" :hide-required-asterisk="true">
              <el-form-item label="邮箱" prop="email">
                <el-input v-model="ruleForm.email" placeholder="请输入邮箱" type="email"></el-input>
              </el-form-item>
              <el-form-item label="内容" prop="text">
                <el-input v-model="ruleForm.text" placeholder="请输入内容"></el-input>
              </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
              <el-button @click="qx" round>取 消</el-button>
              <!-- <el-button type="primary" @click="fs" round>发 送</el-button> -->
              <el-button type="primary" @click="fs" round disabled>接口测试中</el-button>
            </span>
          </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    const checkEmail = (rule, value, cb) => {
      const regEmail = /^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\.[a-zA-Z0-9-]+)*\.[a-zA-Z0-9]{2,6}$/
      if (regEmail.test(value)) {
        return cb()
      }
      cb(new Error('请输入合法的邮箱'))
    }
    return {
      // src: 'https://cube.elemecdn.com/6/94/4d3ea53c084bad6931a56d5158a48jpeg.jpeg',
      srcList: [
        'http://shop.xiaoder.cn/img/dl.png',
        'http://shop.xiaoder.cn/img/sy.png',
        'http://shop.xiaoder.cn/img/lxzz.png',
        'http://shop.xiaoder.cn/img/yhlb.png',
        'http://shop.xiaoder.cn/img/jslb.png',
        'http://shop.xiaoder.cn/img/qxlb.png',
        'http://shop.xiaoder.cn/img/splb.png',
        'http://shop.xiaoder.cn/img/splbadd.png',
        'http://shop.xiaoder.cn/img/flcs.png',
        'http://shop.xiaoder.cn/img/spfl.png',
        'http://shop.xiaoder.cn/img/ddlb.png',
        'http://shop.xiaoder.cn/img/sjbb.png'
      ],
      tableDataA: [
        {
          num: '200',
          test: 'OK',
          text: '请求成功'
        },
        {
          num: '201',
          test: 'CREATED',
          text: '创建成功'
        },
        {
          num: '204',
          test: 'DELETED',
          text: '删除成功'
        },
        {
          num: '400',
          test: 'BAD REQUEST',
          text: '请求的地址不存在或者包含不支持的参数'
        },
        {
          num: '401',
          test: 'UNAUTHORIZED',
          text: '未授权'
        },
        {
          num: '403',
          test: 'FORBIDDEN',
          text: '被禁止访问'
        },
        {
          num: '404',
          test: 'NOT FOUND',
          text: '请求的资源不存在'
        },
        {
          num: '422',
          test: 'Unprocesable entity',
          text: '[POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误'
        },
        {
          num: '500',
          test: 'INTERNAL SERVER ERROR',
          text: '内部错误'
        }
      ],
      tableDataB: [
        { text: '登录界面', test: '界面背景', doc: '采用热门网图' },
        { text: '', test: '账号/密码', doc: '温馨的账号密码提醒' },
        { text: '', test: '提示', doc: '温馨的登录提醒' },
        { text: '首页页面', test: '头像', doc: '以黄金比例0.618计算再结合东方美学展现出圆角效果' },
        { text: '', test: '退出', doc: '判断是否退出和三秒的退出效果' },
        { text: '', test: '面包屑', doc: '尽可能跳转到管理系统的所有功能' },
        { text: '代码区域', test: '浓缩代码', doc: '尽可能的把文件最大化（缩小时出过乱码）' }
      ],
      tableDataC: [
        { text: '登录', test: '验证码功能', doc: '后期项目再次优化解决' },
        { text: '首页', test: '联系作者接口', doc: '跨域问题，普通html文件跨域调用' },
        { text: '角色列表', test: '增删改功能', doc: '后期完善（2022/3/28已完善）' },
        { text: '商品列表', test: '修改功能', doc: '后期完善（2022/3/28已完善）' },
        { text: '添加商品', test: '提交功能', doc: '201/400都可以提交，接口文档默认201，但是400也可以提交，所以提交随缘' },
        { text: '添加商品', test: '换模块/提交功能', doc: '后期添加表单验证语句（2022/3/28已完善）' },
        { text: '添加商品', test: '图片放大', doc: '暂时解决，过程遇到非8888端口和跨域问题' },
        { text: '订单列表', test: '修改地址功能', doc: '功能无click点击事件，仅仅有基本功能，无接口调用（2022/3/28已经修复无点击事件，暂无法put数据到接口）' },
        { text: '订单列表', test: '物流管理', doc: '相关接口无效，无相关JSON' },
        { text: '部分功能', test: '取消按钮失效', doc: '2022/5/20 20/13/14修复' }
      ],
      // 日历
      value: new Date(),
      // 介绍列表
      size: '',
      ruleForm: {},
      fsRules: {
        email: [
          {
            required: true,
            message: '请输入邮箱',
            trigger: 'blur'
          },
          {
            validator: checkEmail,
            trigger: 'blur'
          }
        ],
        text: [
          {
            required: true,
            message: '请输入内容',
            trigger: 'blur'
          },
          {
            min: 1,
            max: 50,
            message: '内容的长度在1~50个字符之间',
            trigger: 'blur'
          }
        ]
      },
      formIf: false,
    }
  },
  created() {},
  methods: {
    tableRowClassName({ row, rowIndex }) {
      if (rowIndex === 1 || rowIndex === 5 || rowIndex === 5) {
        return 'warning-row'
      } else if (rowIndex === 3 || rowIndex === 7) {
        return 'success-row'
      }
      return ''
    },
    close() {
      this.$refs.fsRuleForm.resetFields()
    },
    dj() {
      this.formIf = true
    },
    qx() {
      this.formIf = false
      this.$message.success('取消成功！')
    },
    fsClose() {
      this.$refs.fsRuleForm.resetFields()
    },
    fs() {
      // this.$http.jsonp('http://www.domain2.com:8080/login', {
      //     params: {},
      //     jsonp: 'handleCallback'
      // }).then((res) => {
      //     console.log(res);
      // })
      axios
        .get('https://sctapi.ftqq.com/SCT29496Ti7rU8WefVieOiPJGDnKhrHig.send?title=messagetitle', {
          params: {},
          jsonp: 'handleCallback'
        })
        .then((res) => {
          console.log(res)
        })
      this.formIf = false
      this.$message.success('发送成功！')
    }
  },
  computed: {}
}
</script>

<style lang="less" scoped>
.el-divider__text {
  font-size: 18px;
}
.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  margin: 8px 0;
  border-radius: 4px;
}
.el-image__inner {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.xz {
  margin: 5px 15px;
}
.el-alert {
  margin: 20px 0;
}
.buttonAlas {
  margin-top: 20px;
}
.buttonClass {
  // /* text-align: center; */
  display: block;
  margin: 0 auto;
}
.iframe{
  text-align: center;
  // margin-top: 20px;
}
</style>
