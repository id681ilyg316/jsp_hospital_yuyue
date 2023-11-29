## 本项目实现的最终作用是基于JSP在线医疗预约挂号管理系统
## 分为3个角色
### 第1个角色为管理员角色，实现了如下功能：
 - 医生管理
 - 患者管理
 - 查看排班申请
 - 查看预约折线图
 - 登录
 - 科室信息管理
### 第2个角色为医生角色，实现了如下功能：
 - 修改个人信息
 - 查看患者队列
 - 查看排班
 - 申请停诊
 - 登录
### 第3个角色为用户角色，实现了如下功能：
 - 收到验证码
 - 用户注册
 - 用户登录
 - 科室列表
 - 科室简介
 - 预约
 - 预约成功
 - 首页
## 数据库设计如下：
# 数据库设计文档

**数据库名：** hospital_yuyue

**文档版本：** 


| 表名                  | 说明       |
| :---: | :---: |
| [admin](#admin) |  |
| [apply](#apply) |  |
| [doctor](#doctor) |  |
| [integrity](#integrity) |  |
| [office](#office) |  |
| [patient](#patient) |  |
| [recode](#recode) |  |
| [room](#room) |  |
| [workday](#workday) |  |

**表名：** <a id="admin">admin</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | account |   varchar   | 16 |   0    |    N     |  Y   |       | 账户  |
|  2   | password |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 密码  |
|  3   | name |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 名字  |

**表名：** <a id="apply">apply</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | aid |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | did |   int   | 10 |   0    |    Y     |  N   |   NULL    | 医生id  |
|  3   | dname |   varchar   | 16 |   0    |    Y     |  N   |   NULL    |   |
|  4   | wid |   int   | 10 |   0    |    Y     |  N   |   NULL    |   |
|  5   | reason |   varchar   | 255 |   0    |    Y     |  N   |   NULL    | 原因  |
|  6   | applytime |   datetime   | 19 |   0    |    Y     |  N   |   NULL    | 医生这天上午或下午的号源数  |
|  7   | request |   varchar   | 8 |   0    |    Y     |  N   |   NULL    | 状态：申请出诊，申请停诊  |
|  8   | state |   varchar   | 8 |   0    |    Y     |  N   |   NULL    | 状态：等待处理，同意，拒绝  |

**表名：** <a id="doctor">doctor</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | did |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | account |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 账户  |
|  3   | password |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 密码  |
|  4   | dname |   varchar   | 16 |   0    |    Y     |  N   |   NULL    |   |
|  5   | fee |   int   | 10 |   0    |    Y     |  N   |   NULL    | 医生出诊费  |
|  6   | gender |   varchar   | 2 |   0    |    Y     |  N   |   NULL    | 性别  |
|  7   | age |   tinyint   | 4 |   0    |    Y     |  N   |   NULL    | 年龄  |
|  8   | office |   varchar   | 16 |   0    |    Y     |  N   |   NULL    |   |
|  9   | room |   varchar   | 16 |   0    |    Y     |  N   |   NULL    |   |
|  10   | career |   varchar   | 8 |   0    |    Y     |  N   |   NULL    |   |
|  11   | description |   varchar   | 255 |   0    |    Y     |  N   |   NULL    |   |
|  12   | picpath |   varchar   | 64 |   0    |    Y     |  N   |   NULL    |   |

**表名：** <a id="integrity">integrity</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | integrityid |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | pid |   int   | 10 |   0    |    Y     |  N   |   NULL    | 病人id  |
|  3   | dname |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 医生名字  |
|  4   | office |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 科室名字  |
|  5   | time |   datetime   | 19 |   0    |    Y     |  N   |   NULL    | 诚信记录的时间  |
|  6   | reason |   varchar   | 255 |   0    |    Y     |  N   |   NULL    | 原因  |
|  7   | score |   tinyint   | 4 |   0    |    Y     |  N   |   NULL    | 分值  |

**表名：** <a id="office">office</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | officename |   varchar   | 16 |   0    |    N     |  Y   |       |   |
|  2   | description |   varchar   | 255 |   0    |    Y     |  N   |   NULL    |   |
|  3   | doctornum |   int   | 10 |   0    |    Y     |  N   |   NULL    |   |

**表名：** <a id="patient">patient</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | pid |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | account |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 账户  |
|  3   | email |   varchar   | 255 |   0    |    Y     |  N   |   NULL    | 邮箱  |
|  4   | password |   varchar   | 255 |   0    |    Y     |  N   |   NULL    | 密码  |
|  5   | name |   varchar   | 16 |   0    |    Y     |  N   |   NULL    | 名字  |
|  6   | integrity |   tinyint   | 4 |   0    |    Y     |  N   |   NULL    |   |

**表名：** <a id="recode">recode</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | rid |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | pid |   int   | 10 |   0    |    Y     |  N   |   NULL    | 病人id  |
|  3   | wid |   int   | 10 |   0    |    Y     |  N   |   NULL    | 工作日id  |
|  4   | did |   int   | 10 |   0    |    Y     |  N   |   NULL    | 医生id  |
|  5   | serialnumber |   int   | 10 |   0    |    Y     |  N   |   NULL    | 就诊序号  |
|  6   | visitdate |   date   | 10 |   0    |    Y     |  N   |   NULL    | 就诊日期  |
|  7   | visitnoon |   varchar   | 4 |   0    |    Y     |  N   |   NULL    | 就诊上午或下午  |
|  8   | visittime |   time   | 8 |   0    |    Y     |  N   |   NULL    | 就诊时间  |
|  9   | ordertime |   datetime   | 19 |   0    |    Y     |  N   |   NULL    | 预约记录的时间  |
|  10   | state |   varchar   | 8 |   0    |    Y     |  N   |   NULL    | 预约状态：成功，取消，完成，爽约  |

**表名：** <a id="room">room</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | id |   varchar   | 255 |   0    |    Y     |  N   |   NULL    | ID  |
|  2   | officename |   varchar   | 255 |   0    |    Y     |  N   |   NULL    |   |
|  3   | roomname |   varchar   | 255 |   0    |    Y     |  N   |   NULL    |   |
|  4   | doctornum |   int   | 10 |   0    |    Y     |  N   |   NULL    |   |

**表名：** <a id="workday">workday</a>

**说明：** 

**数据列：**

| 序号 | 名称 | 数据类型 |  长度  | 小数位 | 允许空值 | 主键 | 默认值 | 说明 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|  1   | wid |   int   | 10 |   0    |    N     |  Y   |       |   |
|  2   | did |   int   | 10 |   0    |    Y     |  N   |   NULL    | 医生id  |
|  3   | worktime |   varchar   | 4 |   0    |    Y     |  N   |   NULL    | 医生工作日，星期几  |
|  4   | ampm |   varchar   | 4 |   0    |    Y     |  N   |   NULL    | 医生工作日的上午或下午  |
|  5   | nsnum |   int   | 10 |   0    |    Y     |  N   |   NULL    | 医生这天上午或下午的号源数  |
|  6   | state |   varchar   | 8 |   0    |    Y     |  N   |   NULL    | 状态：已满，预约，停诊  |

**运行不出来可以微信 javape 我的公众号：源码码头**
