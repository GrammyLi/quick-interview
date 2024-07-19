### 需求背景

专门做面试记录，别人也可以看对应面试记录，增加面试通过率

### 需求拆分

1. 用户登录、注册
2. 用户投稿
3. 首页显示所有面经
4. 留言板，给网站留下意见

### 数据库设计

#### 用户表 (users)

| 字段名    | 类型     | 备注     |
| --------- | -------- | -------- |
| id        | int      | 主键     |
| ct        | datetime | 创建时间 |
| ut        | datetime | 更新时间 |
| username  | str      | 用户名   |
| password  | str      | 密码     |
| email     | str      | 邮箱     |
| signature | str      | 个性签名 |

#### 会话表 (sessions)

| 字段名  | 类型     | 备注       |
| ------- | -------- | ---------- |
| id      | int      | 主键       |
| ct      | datetime | 创建时间   |
| ut      | datetime | 更新时间   |
| user_id | int      | 用户 ID    |
| token   | str      | 会话 token |

#### 面经表 (interviews)

| 字段名    | 类型     | 备注     |
| --------- | -------- | -------- |
| id        | int      | 主键     |
| ct        | datetime | 创建时间 |
| ut        | datetime | 更新时间 |
| user_id   | int      | 用户 ID  |
| user_name | str      | 用户名   |
| title     | str      | 面经标题 |
| content   | text     | 面经内容 |
| view      | int      | 查看次数 |

#### 职业表 (careers)

| 字段名 | 类型     | 备注     |
| ------ | -------- | -------- |
| id     | int      | 主键     |
| ct     | datetime | 创建时间 |
| ut     | datetime | 更新时间 |
| name   | str      | 职业名称 |

#### 留言板表 (feedback)

| 字段名  | 类型     | 备注     |
| ------- | -------- | -------- |
| id      | int      | 主键     |
| ct      | datetime | 创建时间 |
| ut      | datetime | 更新时间 |
| user_id | int      | 用户 ID  |
| content | text     | 留言内容 |

####  接口设计

#### 用户登录

- URL: `/api/login`
- 方法: `POST`
- 参数:
  - `username`: 用户名
  - `password`: 密码
- 返回:
  - `token`: 认证 token

#### 用户注册

- URL: `/api/register`
- 方法: `POST`
- 参数:
  - `username`: 用户名
  - `password`: 密码
  - `email`: 邮箱
- 返回:
  - `message`: 注册成功信息

#### 获取所有面经

- URL: `/api/interviews`
- 方法: `GET`
- 返回:
  - `interviews`: 面经列表

#### 发布面经

- URL: `/api/interview`
- 方法: `POST`
- 参数:
  - `title`: 面经标题
  - `content`: 面经内容
- 返回:
  - `message`: 发布成功信息

#### 获取面经详情

- URL: `/api/interview/<id>`
- 方法: `GET`
- 返回:
  - `interview`: 面经详情

#### 发布留言

- URL: `/api/feedback`
- 方法: `POST`
- 参数:
  - `content`: 留言内容
- 返回:
  - `message`: 发布成功信息

#### 获取所有留言

- URL: `/api/feedbacks`
- 方法: `GET`
- 返回:
  - `feedbacks`: 留言列表

### 技术栈

- **后端**:
  - 语言: Python
  - 框架: Flask
  - ORM: SQLAlchemy
- **前端**:
  - 框架: React
  - UI 库: Ant Design
  - TypeScirpt
