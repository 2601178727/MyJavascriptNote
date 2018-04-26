## export  应用详解

```
/*
    1. 名字导出 使用时 导入的变量名必须和导出的名称一致
    import { nameExport } from './fetch/learnExport'
*/

export function nameExport (x, y) {
  return x * y
}

```

```
/*
2. 列表导出 使用时 需要特殊处理 console.log(learnExport.add(1, 2))
import * as learnExport from './fetch/learnExport'
*/
const use = ['张三', '李四', '王二麻子']
function add (x, y) {
return x + y
}

export { use, add }


```

```
/*
3. 默认导出 一个模块只能有一个默认导出，
对于默认导出，导入的名称可以和导出的名称不一致，这对于导出匿名函数或类非常有用。
import bts from './fetch/learnExport'
console.log(bts())

也可以组合使用
import bts, { nameExport } from './fetch/learnExport'
console.log(bts())
console.log(nameExport(1, 3))
*/
export default function () {
return 1
}


```

    /*
    4. 重命名 为了解决导出命名冲突的问题，ES6为你提供了重命名的方法解决这个问题
    这两个模块都会导出以`flip`命名的东西。
    要同时导入两者，我们至少要将其中一个的名称改掉。
    import {flip as flipOmelet} from "eggs.js"
    import {flip as flipHouse} from "real-estate.js"
    */

    /*
    5.当你在导出的时候也可以重命名。你可能会想用两个不同的名称导出相同的值，这样的情况偶尔也会遇到
    function v1() { ... }
    function v2() { ... }

    export {
    v1 as streamV1,
    v2 as streamV2,
    v2 as streamLatestVersion
    }
    */



