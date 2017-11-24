> export defaule 必须拥有自己的return，否则在调用的时候不会拿到值

```
错误姿势：
export const userRole = (role) => {
  switch (role) {
    case '超级管理员':
      role = 'SUPER_ADMIN'
      break
    case '产品经理':
      role = 'PM_ADMIN'
      break
    case '项目主任':
      role = 'PROJECT_SUPERVISOR'
      break
    case '企业管理员':
      role = 'BUSINESS_MANAGER'
      break
    case '班主任':
      role = 'HEADTEACHER'
      break
    case '学员':
      role = 'STUDENT'
      break
    default:
      return 1
  }
}

export default userRole

```



```
正确姿势：
export const userRole = (role) => {
  let roles = null
  switch (role) {
    case '超级管理员':
      roles = 'SUPER_ADMIN'
      break
    case '产品经理':
      roles = 'PM_ADMIN'
      break
    case '项目主任':
      roles = 'PROJECT_SUPERVISOR'
      break
    case '企业管理员':
      roles = 'BUSINESS_MANAGER'
      console.log(role)
      break
    case '班主任':
      roles = 'HEADTEACHER'
      break
    case '学员':
      roles = 'STUDENT'
      break
    default:
      return 1
  }
  return roles
}

export default userRole

```



