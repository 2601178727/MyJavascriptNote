> 关键词 dialogFormVisible 、 showDialog、this.$emit\('update:showDialog', false\)
>
> 思路：组件中dialogFormVisible 的值未true、false会影响到对话框的显示和隐藏
>
> 那么如果想要在父组件中showDialog操作子组件的值就需要传值、并通过watch来监听变化执行函数
>
> 此时就需要用到props配合父组件引用时传值
>
> 同样的如果想要在子组件执行完操作后将父组件的值还原，就需要向父组件传值
>
> 此时就需要用到this.$emit\('update:showDialog', false\)



子组件

```
@HTML
<el-dialog
		:title="this.title"
		:modal="true"
		:close-on-click-modal="true"
		:close-on-press-escape="false"
		:show-close="false"
		:visible.sync="dialogVisible"
		:before-close="handleClose">
	<el-form
            :model="formValue"
            :rules="rules"
            ref="ruleForm"
            class="demo-ruleForm">
                <el-form-item
                prop="cname">
                    <el-input 
                    auto-complete="off"
                    placeholder="请输入中文名称"
                    v-model="formValue.cname">
                    </el-input>
                    <div class="read">
                        <span>（请输入不超过10个汉字）</span>
                    </div>
                </el-form-item>
                <el-form-item
                prop="ename">
                    <el-input 
                    auto-complete="off"
                    placeholder="请输入中文名称"
                    v-model="formValue.ename">
                    </el-input>
                    <div class="read">
                        <span>（请输入不超过30个英文字母）</span>
                    </div>
                </el-form-item> 
	</el-form>
        <div slot="footer" class="dialog-footer">
          <el-button @click="cancelBtn('formValue')">取消</el-button>
          <el-button type="danger" @click="certainBtn('formValue')">确定</el-button>
        </div>
</el-dialog>
```

    @JS
    import DialogForm from './../../components/AddDialog/index'

    export default {
        data () {
        let cnameRule = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('中文名称不能为空'))
          }
        }
        let enameRule = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('英文名称不能为空'))
          }
        }
        return {
                dialogVisible: false,
              rules: {
                cname: [
                  { validator: cnameRule, trigger: 'blur' }
                ],
                ename: [
                  { validator: enameRule, trigger: 'blur' }
                ]
              }
            }
        },
        props: {
          showDialog: Boolean,
          title: String,
          formValue: Object,
          loadList2: Function
        },
        methods: {
        cancelBtn (formName) {
          this.$refs[formName].resetFields()
          this.dialogVisible = false
          this.$emit('update:showDialog', false)
        },
        certainBtn (formName) {
          this.$refs[formName].validate((valid) => {
            if (valid) {
              this.dialogVisible = false
              this.$emit('update:showDialog', false)
              let formData = {
                topic_id: this.$route.query.topic_id,
                ctitle: this.formValue.cname,
                etitle: this.formValue.ename
              }
              API.post('api/discussion/new', formData)
                .then((res) => {
                  console.log(res)
                  if (res.data.code !== 1) {
                    this.$message.error(`${res.data.message}`)
                  } else {
                    this.$message({
                      message: `${res.data.message}`,
                      type: 'success'
                    })
                  }
                  this.loadList2()
                })
            } else {
              console.log('error submit!!')
              return false
            }
          })
        }
      },
      watch: {
        showDialog: function () {
          this.dialogVisible = this.showDialog
        }
      }
    }




父组件

```
@HTML
<el-button 
          type="text"
          class="add-to-btn"
          @click="showDialogForm">
            添加新讨论
</el-button>
<DialogForm
          :showDialog="showDialog"
          :title="title"
          :formValue="formValue"
          :showDialog.sync="showDialog">
</DialogForm>
```

```
@JS
import DialogForm from './../../components/AddDialog/index'

export default {
    components: { DialogForm },
    data () {
    return {
            formValue: {
                cname: '',
                ename: ''
            },
            title: '添加新讨论',
            showDialog: false
        }
    }
}

```



