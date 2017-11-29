**this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁**，**实际上this的最终指向的是那个调用它的对象**

    viewData: [
            {
              type: '1-2',
              prop: 'companyName',
              label: '账户名称',
              width: '10%',
              align: 'center',
              inputShow: false,
              inputShowFn: () => {
                this.viewData[2].inputShow = true
              },
              inputValue: '',
              renderHeader: (createElement) => {
                let self = this
                console.log(self, 2222) 
                //这里的this指向的就是viewData，这里用了es6的语法 也可写出renderHeader： function () {}
                //如果写出renderHeader (createElement) {} 就会出错，因为没有key值，那么他的this指向的就是他本身
                return createElement('div', {
                  domProps: {
                    innerHTML: `
                    <span class="accoundNameSpan">账户名称</span>
                    <input type="text" class="accoundNameInput">
                    `
                  },
                  style: {
                    padding: '0',
                    lineHeight: '1',
                    marginTop: '5px',
                    width: '100%'
                  },
                  on: {
                    '!click': function (e) {
                      let span = document.getElementsByClassName('accoundNameSpan')[0]
                      let input = document.getElementsByClassName('accoundNameInput')[0]
                      span.style.display = 'none'
                      input.style.display = 'inline-block'
                      event.stopPropagation()
                    },
                    input: function (event) {
                      self.value = event.target.value
                      self.$emit('div', event.target.value)
                      console.log(self)
                    }
                  }
                })
              }
            }
          ]



