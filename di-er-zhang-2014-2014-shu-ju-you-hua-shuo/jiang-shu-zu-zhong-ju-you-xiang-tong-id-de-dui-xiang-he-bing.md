> 将下面数组中具有相同lesson_id的对象合并，如果lang为1，将lesson_\_name的值赋值给ename并存储，如果lang为2，将_lesson_\_name的值赋值给cname并存储，数组的排序顺序根据number的值排序

![](/assets/import.png)

```
API.post('api/lesson/list', formData)
        .then((res) => {
          let newData = res.data.data.items
          let newObj = {}
          newData.forEach(function (element) {
            this.num = element.number
            if (typeof newObj[element.number] === 'undefined') {
              newObj[element.number] = {
                id: element.lesson_id,
                cname: '',
                ename: '',
                number: element.number
              }
            }
            newObj[element.number][element.lang === 1 ? 'ename' : 'cname'] = element.lesson_name
            /**
             * console.log(newObj[1]['cname'])
             * 相当于newObj[1].cname
             */
          }, this)
          for (let i = 0; i < newObj.length; i++) {
            if (newObj[i] === '' || typeof (newObj[i]) === 'undefined') {
              newObj.splice(i, 1)
              i = i - 1
            }
          }
          let arr1 = []
          for (let item in newObj) {
            let obj1 = {
              id: newObj[item].id,
              cDate: newObj[item].cname,
              eDate: newObj[item].ename
            }
            arr1.push(obj1)
          }
          this.tableData = arr1
        })
```



