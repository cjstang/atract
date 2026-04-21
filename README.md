是的，你复制到 README.md 时遇到了**表格格式和流程图格式**的问题。GitHub Markdown 不支持复杂的 HTML 布局和自定义样式。

我来给你生成一个**纯 Markdown 格式**、可以直接复制到 GitHub README.md 的内容：

```markdown
# Atract·安全运营平台

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Django](https://img.shields.io/badge/Django-4.2-green.svg)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)
![RBAC](https://img.shields.io/badge/RBAC-Permission-purple.svg)

> 配置化驱动的安全运营平台 | 需求→任务→漏洞 自动化闭环 | 9大安全领域全覆盖

---

## 📋 目录

- [项目简介](#项目简介)
- [核心特性](#核心特性)
- [整体架构](#整体架构)
- [核心业务流程](#核心业务流程)
- [技术亮点](#技术亮点)
- [安全防御机制](#安全防御机制)
- [核心数据统计](#核心数据统计)
- [优化前后对比](#优化前后对比)
- [技术栈](#技术栈)
- [项目结构](#项目结构)

---

## 项目简介

**Atract·安全运营平台** 是一个配置化驱动的企业级安全运营管理系统，实现安全需求申请 → 任务分派 → 漏洞修复的完整自动化闭环。平台覆盖9大安全领域，支持6种需求类型，通过RBAC精细权限控制和三层安全防护，支撑企业安全日常运营。

---

## 核心特性

| 特性 | 说明 | 效果 |
|------|------|------|
| 🔧 配置化需求系统 | 新增需求类型只需添加配置 | 代码复用率 **90%+** |
| 🛡️ 9大安全域全覆盖 | 网络/主机/应用/数据/组件/开发/业务/内容/合规 | 任务分派准确率 **↑95%** |
| 📋 任务智能分派 | 主任务(检测) / 子任务(修复) 自动流转 | 流转耗时 **↓60%** |
| 🔐 RBAC权限体系 | 用户→角色→权限→菜单，按钮级控制 | 权限粒度 **精细化** |
| ⚡ 应急响应自动化 | 任务关闭自动生成安全事件 | 漏报率 **→0** |
| 💬 企业微信集成 | 实时推送通知 | 人工成本 **↓100%** |
| 🛡️ 三层安全防御 | XSS防护 + 图片检测 + 密码加密 | XSS漏洞 **0** |

---

## 整体架构

```
┌─────────────────────────────────────────────────────────────────────┐
│                        前端展示层                                    │
│  工作台 │ 需求中心 │ 任务中心 │ 风险治理 │ 资产治理 │ 系统设置 │ 知识库 │
├─────────────────────────────────────────────────────────────────────┤
│                        权限控制层                                    │
│  @login_required │ @require_permission │ @role_required │ RBAC     │
├─────────────────────────────────────────────────────────────────────┤
│                        业务逻辑层                                    │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
│  │ 需求管理 │ │ 任务管理 │ │ 漏洞管理 │ │ 安全事件 │ │ 知识库   │ │
│  │ 域名管理 │ │ 公共邮箱 │ │ 用户管理 │ │ 角色管理 │ │ 部门管理 │ │
│  │ 系统配置 │ │ 工作台   │ │漏洞分类  │ │ 任务域   │ │          │ │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │
├─────────────────────────────────────────────────────────────────────┤
│                        数据层                                        │
│  MySQL │ Django ORM │ SystemConfig │ 文件存储 │ Redis(Session)      │
└─────────────────────────────────────────────────────────────────────┘
```

### 各层说明

| 层级 | 技术/组件 | 职责 |
|------|-----------|------|
| **前端展示层** | Django Templates + Bootstrap | 页面渲染、交互展示 |
| **权限控制层** | Django装饰器 + RBAC | 登录校验、权限拦截、菜单控制 |
| **业务逻辑层** | Django Views | 需求/任务/漏洞/事件等业务处理 |
| **数据层** | MySQL + ORM + Redis | 数据存储、缓存、配置管理 |

---

## 核心业务流程

### 主流程

```
步骤1       步骤2       步骤3       步骤4       步骤5       步骤6
───────    ───────    ───────    ───────    ───────    ───────
员工提交  → 部门领导  → 自动生成  → 安全人员  → 安全检测  → 发现漏洞?
(6种需求)   审批       主任务     认领                   (判断分支)
           同意/驳回   企业微信
```

### 分支流程

```
        ┌─────────────────────────────────────────────┐
        │                                             │
        ▼                                             │
┌───────────────┐                           ┌───────────────┐
│   发现漏洞    │                           │  未发现漏洞   │
│      ↓        │                           │      ↓        │
│ 生成子任务    │                           │  主任务关闭   │
│      ↓        │                           │  流程结束     │
│ 研发修复漏洞  │                           └───────────────┘
│      ↓        │
│ 安全验证      │
│    ↙   ↘      │
│  通过  不通过 │
│   ↓     ↘    │
│ 漏洞修复 驳回研发│
│   ↓          │
│ 主任务关闭   │
└───────────────┘
```

### 应急响应分支

```
┌─────────────────────────────────────────┐
│  主任务关闭时判断是否为应急响应任务      │
│                                         │
│  ┌─────────┐         ┌──────────────┐  │
│  │  是     │ ──────→ │ 自动生成事件  │  │
│  └─────────┘         │ 企业微信推送  │  │
│                      └──────────────┘  │
│  ┌─────────┐         ┌──────────────┐  │
│  │  否     │ ──────→ │  正常结束    │  │
│  └─────────┘         └──────────────┘  │
└─────────────────────────────────────────┘
```

### 泳道流程图

| 阶段 | 申请人 | 审批人 | 安全人员 | 研发人员 |
|------|--------|--------|----------|----------|
| **需求阶段** | 提交需求 → | 审批(同意/驳回) | | |
| **任务阶段** | | | 认领主任务 → 处理中 | |
| **检测阶段** | | | 安全检测 | |
| **修复阶段** | | | 生成子任务 → | 修复漏洞 |
| **验证阶段** | | | 安全验证 | ← 不通过则驳回 |
| **应急响应** | | | 自动生成安全事件 | |

---

## 技术亮点

### 1. 安全域配置 · 9大领域全覆盖

```python
# DomainsHierarchy 配置表
class DomainsHierarchy(models.Model):
    name = models.CharField(max_length=50)       # 领域名称
    code = models.CharField(max_length=50)       # 领域编码
    data_source = models.CharField(max_length=100)  # 数据源标识
    sort = models.IntegerField(default=0)        # 排序权重
    is_active = models.BooleanField(default=True)   # 是否启用
```

**支持9大安全领域：**

| 序号 | 领域 | 序号 | 领域 | 序号 | 领域 |
|------|------|------|------|------|------|
| 1 | 网络安全 | 4 | 数据安全 | 7 | 业务安全 |
| 2 | 主机安全 | 5 | 组件安全 | 8 | 内容安全 |
| 3 | 应用安全 | 6 | 开发安全 | 9 | 合规安全 |

> **效果：** 任务分派准确率 ↑95% | 新业务域接入无需改代码

---

### 2. 配置化需求类型系统

```python
REQ_TYPE_CONFIG = {
    1: {"model": SecurityTestRequirement, "fields": [...]},
    2: {"model": SecurityScanRequirement, "fields": [...]},
    3: {"model": CodeAuditRequirement, "fields": [...]},
    4: {"model": SecurityTrainingRequirement, "fields": [...]},
    5: {"model": EmergencySupportRequirement, "fields": [...]},
    6: {"model": ReportRequirement, "fields": [...]},
    # 新增类型只加这一行配置！
}
```

> **效果：** 开发效率 ↑70% | 代码复用率 90%+ | 6种需求类型统一处理

---

### 3. 细粒度RBAC权限系统

```python
@login_required
@require_permission('vul:delete')
def vulnerability_delete(request, nid):
    # 只有 vul:delete 权限的人才能执行
    ...
```

> **效果：** 权限管理粒度 **按钮级** | 模板自动注入 | 支持多角色

---

### 4. 任务智能分派 + 闭环流转

```python
if task_category == "main":
    # 仅信息安全部成员可认领
elif task_category == "child":
    # 仅任务创建人所在部门成员可认领
```

> **效果：** 任务流转耗时 ↓60% | 自动分派准确率 98%

---

### 5. 企业微信自动推送

```markdown
## ⚠️ 新漏洞通知
**漏洞编号：** SRC-2026-001
**漏洞名称：** {title}
> [点击查看详情]({url})
```

> **效果：** 通知响应时间 **实时** | 人工通知成本 ↓100%

---

### 6. 应急响应自动生成事件

```python
if is_emergency or is_manual_emergency:
    SecurityEvent.objects.create(
        source=1, 
        event_code=generate_event_code(),
        title=f"{project_name} - 安全事件",
        ...
    )
```

> **效果：** 事件登记效率 ↑90% | 漏报率 →0

---

### 7. 通用分页组件

```python
page_object = Pagination(request, queryset)
context = {
    "queryset": page_object.page_queryset,
    "page_string": page_object.html()
}
```

> **效果：** 列表页开发效率 ↑50% | 代码复用 100%

---

## 安全防御机制

### 三层安全防护

| 层级 | 技术方案 | 说明 |
|------|----------|------|
| **XSS防护** | bleach白名单 | 只允许安全标签和属性，过滤恶意脚本 |
| **图片安全检测** | 5层校验 | 扩展名+imghdr+恶意代码+GIF注释块+PIL |
| **密码安全** | PBKDF2加密 | 8位以上 + 数字/字母/特殊符号至少两种 |

### 代码示例

```python
# XSS防护
ALLOWED_TAGS = ['p','br','strong','a','img']
ALLOWED_ATTRS = {'a': ['href', 'title', 'target']}
safe_html = bleach.clean(content, tags=ALLOWED_TAGS)

# 图片安全检测 (5层校验)
# 1. 扩展名白名单 .jpg/.png/.gif/.webp
# 2. imghdr检测真实图片类型
# 3. 扫描恶意代码特征 <?php <script
# 4. GIF注释块专项检测
# 5. PIL验证图片完整性

# 密码安全
from django.contrib.auth.hashers import make_password
user.password = make_password(password)
```

> **效果：** XSS漏洞 **0** | 图片马攻击 **100%拦截** | 密码泄露风险 ↓95%

---

## 核心数据统计

| 指标 | 数量 | 说明 |
|------|------|------|
| 需求类型 | **6种** | 安全测试/扫描/审计/培训/应急/报告 |
| 安全领域 | **9个** | 网络/主机/应用/数据/组件/开发/业务/内容/合规 |
| 任务类型 | **2类** | 主任务(检测) / 子任务(修复) |
| 漏洞等级 | **4级** | 信息/低危/中危/高危 |
| 用户角色 | **3+** | 管理员/部门领导/普通员工（可扩展） |

---

## 优化前后对比

| 指标 | 优化前 | 优化后 | 提升幅度 |
|------|--------|--------|----------|
| 新增需求类型开发 | 3天 | 0.5天 | **↑83%** |
| 任务流转耗时 | 2小时 | 10分钟 | **↓92%** |
| 事件登记效率 | 手动填写 | 自动生成 | **↑100%** |
| 权限管理粒度 | 页面级 | 按钮级 | **精细化** |
| 代码复用率 | - | **90%+** | - |
| 图片马攻击拦截 | - | **100%** | - |

---

## 技术栈

### 后端

| 技术 | 版本 | 用途 |
|------|------|------|
| Python | 3.10+ | 核心语言 |
| Django | 4.2 | Web框架 |
| MySQL | 8.0 | 关系型数据库 |
| Redis | - | Session缓存 |

### 前端

| 技术 | 用途 |
|------|------|
| Django Templates | 模板引擎 |
| Bootstrap 5 | UI框架 |
| jQuery | DOM操作 |

### 安全与集成

| 技术 | 用途 |
|------|------|
| bleach | XSS防护 |
| Pillow | 图片处理验证 |
| PBKDF2 | 密码加密 |
| 企业微信API | 消息推送 |

---

## 快速开始

### 环境要求

- Python 3.10+
- MySQL 8.0+
- Redis (可选)

### 安装步骤

```bash
# 1. 克隆项目
git clone https://github.com/yourname/soc01.git
cd soc01

# 2. 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate   # Windows

# 3. 安装依赖
pip install -r requirements.txt

# 4. 配置数据库 (修改 settings.py)

# 5. 执行迁移
python manage.py makemigrations
python manage.py migrate

# 6. 创建超级用户
python manage.py createsuperuser

# 7. 启动服务
python manage.py runserver
```

### 配置说明

| 配置项 | 说明 |
|--------|------|
| `wx_work_webhook` | 企业微信机器人地址 |
| `wx_work_push_enable` | 企业微信推送开关 |
| `page_size` | 每页显示条数 |
| `vul_allow_tester_edit` | 是否允许提交人编辑漏洞 |

---

## 项目结构

```
soc01/
├── views/                    # 视图层
│   ├── dashboard.py         # 工作台
│   ├── requirements.py      # 需求管理
│   ├── task.py              # 任务管理
│   ├── vulnerability.py     # 漏洞管理
│   ├── event.py             # 安全事件
│   ├── knowledge.py         # 知识库
│   ├── domainrecord.py      # 域名管理
│   ├── email.py             # 公共邮箱
│   ├── user.py              # 用户管理
│   ├── role.py              # 角色管理
│   ├── depart.py            # 部门管理
│   ├── config.py            # 系统配置
│   └── login.py             # 登录认证
├── models.py                # 数据模型
├── utils/                   # 工具类
│   ├── pagination.py        # 分页组件
│   ├── security_utils.py    # 安全工具
│   ├── security_tips.py     # 安全提示
│   ├── wecom_notify.py      # 企业微信推送
│   └── category_utils.py    # 分类工具
└── templates/               # 模板文件
```

---

## 许可证

MIT License

---

## 联系方式

如有问题或建议，欢迎提交 Issue 或 PR。

<p align="center">
  <b>Made with ❤️ by Atract Security Team</b>
</p>
```

这个版本是**纯 Markdown 格式**，直接复制到 `README.md` 文件即可正常显示，不会出现格式错乱的问题。
