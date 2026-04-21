我已经为你**优化成标准、美观、可直接用于 GitHub 的 README 格式**，修复了链接、排版、图标、结构，完全符合开源项目规范，**复制即可直接使用**：

```markdown
# Atract · 安全运营平台

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Django](https://img.shields.io/badge/Django-4.2-green.svg)
![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)
![RBAC](https://img.shields.io/badge/RBAC-Permission-purple.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

> 配置化驱动的企业级安全运营平台 | 需求→任务→漏洞 自动化闭环 | 9大安全领域全覆盖

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
- [快速开始](#快速开始)
- [项目结构](#项目结构)
- [许可证](#许可证)

---

## 项目简介

**Atract·安全运营平台** 是一个基于配置化驱动设计的企业级安全运营管理系统，实现**安全需求申请 → 任务智能分派 → 漏洞闭环修复**的全流程自动化。

平台覆盖 **9 大安全领域**，支持 **6 种需求类型**，通过 RBAC 细粒度权限控制与三层安全防护体系，为企业安全日常运营提供稳定、高效、可扩展的支撑能力。

---

## 核心特性

| 特性 | 说明 | 效果 |
|------|------|------|
| 🔧 配置化需求系统 | 新增需求类型仅需添加配置，无需修改业务代码 | 代码复用率 **90%+** |
| 🛡️ 9大安全域全覆盖 | 网络/主机/应用/数据/组件/开发/业务/内容/合规 | 任务分派准确率 **↑95%** |
| 📋 任务智能分派 | 主任务(检测)/子任务(修复) 自动流转与权限控制 | 流转耗时 **↓60%** |
| 🔐 RBAC权限体系 | 用户→角色→权限→菜单，支持**按钮级**权限控制 | 权限管理**精细化** |
| ⚡ 应急响应自动化 | 任务关闭自动生成安全事件，无需人工登记 | 漏报率 **→0** |
| 💬 企业微信集成 | 漏洞/任务实时推送通知 | 人工通知成本 **↓100%** |
| 🛡️ 三层安全防御 | XSS防护 + 图片木马检测 + 高强度密码加密 | XSS漏洞 **0** |

---

## 整体架构

![整体架构](https://github.com/user-attachments/assets/ca8cee50-76f0-4bc2-b15b-4bcb2e5b799f)

---

## 核心业务流程

**需求 → 任务 → 漏洞 完整自动化闭环**
应急响应任务自动生成安全事件

![核心业务流程](https://github.com/user-attachments/assets/8d2fc023-e958-4653-af4a-0cfd8ac46971)

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
1. 网络安全 4. 数据安全 7. 业务安全
2. 主机安全 5. 组件安全 8. 内容安全
3. 应用安全 6. 开发安全 9. 合规安全

> 效果：任务分派准确率 ↑95% | 新业务域接入无需修改代码

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
    # 新增类型只加一行配置！
}
```

> 效果：开发效率 ↑70% | 代码复用率 90%+ | 6种需求统一处理

---

### 3. 细粒度 RBAC 权限系统
```python
@login_required
@require_permission('vul:delete')
def vulnerability_delete(request, nid):
    # 仅拥有 vul:delete 权限的用户可执行
    ...
```

> 效果：按钮级权限控制 | 模板自动注入 | 支持多角色切换

---

### 4. 任务智能分派 + 闭环流转
```python
if task_category == "main":
    # 仅信息安全部成员可认领
elif task_category == "child":
    # 仅任务创建人所在部门成员可认领
```

> 效果：任务流转耗时 ↓60% | 自动分派准确率 98%

---

### 5. 企业微信实时推送
```markdown
## ⚠️ 新漏洞通知
**漏洞编号：** SRC-2026-001
**漏洞名称：** {title}
> [点击查看详情]({url})
```

> 效果：实时通知 | 人工通知成本降至 0

---

### 6. 应急响应自动生成安全事件
```python
if is_emergency or is_manual_emergency:
    SecurityEvent.objects.create(
        source=1, 
        event_code=generate_event_code(),
        title=f"{project_name} - 安全事件",
        ...
    )
```

> 效果：事件登记效率 ↑90% | 漏报率 → 0

---

### 7. 通用分页组件
```python
page_object = Pagination(request, queryset)
context = {
    "queryset": page_object.page_queryset,
    "page_string": page_object.html()
}
```

> 效果：列表页开发效率 ↑50% | 代码复用 100%

---

## 安全防御机制

### 三层安全防护

| 防护层级 | 技术方案 | 说明 |
|---------|----------|------|
| **XSS 防护** | bleach 白名单过滤 | 仅允许安全标签，彻底拦截恶意脚本 |
| **图片安全检测** | 5 层深度校验 | 扩展名+真实类型+恶意代码+GIF注释+PIL完整性 |
| **密码安全** | PBKDF2 强加密 | 8位以上+组合复杂度，不可逆存储 |

### 核心防御代码
```python
# XSS 防护
ALLOWED_TAGS = ['p','br','strong','a','img']
ALLOWED_ATTRS = {'a': ['href', 'title', 'target']}
safe_html = bleach.clean(content, tags=ALLOWED_TAGS)

# 图片安全检测（5层校验）
# 1. 扩展名白名单  2. imghdr 真实类型校验
# 3. 恶意代码扫描  4. GIF 注释块检测  5. PIL 完整性校验

# 密码加密
from django.contrib.auth.hashers import make_password
user.password = make_password(password)
```

> 效果：XSS 漏洞 0 | 图片木马 100% 拦截 | 密码泄露风险 ↓95%

---

## 核心数据统计

| 指标 | 数量 | 说明 |
|------|------|------|
| 需求类型 | **6 种** | 安全测试/扫描/审计/培训/应急/报告 |
| 安全领域 | **9 个** | 全覆盖企业安全场景 |
| 任务类型 | **2 类** | 主任务(检测) / 子任务(修复) |
| 漏洞等级 | **4 级** | 信息/低危/中危/高危 |
| 用户角色 | **3+** | 管理员/部门领导/普通员工（支持扩展） |

---

## 优化前后对比

| 指标 | 优化前 | 优化后 | 提升幅度 |
|------|--------|--------|----------|
| 新增需求类型开发 | 3 天 | 0.5 天 | **↑83%** |
| 任务流转耗时 | 2 小时 | 10 分钟 | **↓92%** |
| 事件登记效率 | 手动填写 | 自动生成 | **↑100%** |
| 权限管理粒度 | 页面级 | 按钮级 | **精细化** |
| 代码复用率 | - | **90%+** | - |
| 图片木马拦截 | - | **100%** | - |

---

## 技术栈

### 后端
| 技术 | 版本 | 用途 |
|------|------|------|
| Python | 3.10+ | 核心开发语言 |
| Django | 4.2 | Web 开发框架 |
| MySQL | 8.0 | 关系型数据库 |
| Redis | - | Session 缓存 |

### 前端
| 技术 | 用途 |
|------|------|
| Django Templates | 模板引擎 |
| Bootstrap 5 | UI 框架 |
| jQuery | 前端交互 |

### 安全与集成
| 技术 | 用途 |
|------|------|
| bleach | XSS 防护 |
| Pillow | 图片安全验证 |
| PBKDF2 | 密码加密 |
| 企业微信 API | 消息推送 |

---

## 快速开始

### 环境要求
- Python 3.10+
- MySQL 8.0+
- Redis（可选）

### 安装部署
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

# 4. 修改 settings.py 配置数据库

# 5. 执行数据库迁移
python manage.py makemigrations
python manage.py migrate

# 6. 创建超级管理员
python manage.py createsuperuser

# 7. 启动项目
python manage.py runserver
```

### 关键配置
| 配置项 | 说明 |
|--------|------|
| `wx_work_webhook` | 企业微信机器人 WebHook |
| `wx_work_push_enable` | 消息推送开关 |
| `page_size` | 列表分页条数 |
| `vul_allow_tester_edit` | 提交人是否可编辑漏洞 |

---

## 项目结构

```
soc01/
├── views/                    # 业务视图层
│   ├── dashboard.py         # 工作台
│   ├── requirements.py      # 需求管理
│   ├── task.py              # 任务管理
│   ├── vulnerability.py     # 漏洞管理
│   ├── event.py             # 安全事件
│   ├── knowledge.py         # 知识库
│   ├── domainrecord.py      # 域名管理
│   ├── email.py             # 公共邮箱
│   ├── user.py              # 用户管理
│   ├── role.py              # 角色权限
│   ├── depart.py            # 部门管理
│   ├── config.py            # 系统配置
│   └── login.py             # 登录认证
├── models.py                # 数据模型
├── utils/                   # 通用工具类
│   ├── pagination.py        # 分页组件
│   ├── security_utils.py    # 安全工具
│   ├── wecom_notify.py      # 企业微信推送
│   └── category_utils.py    # 分类工具
└── templates/               # 前端模板
```

---

## 许可证

本项目基于 **MIT License** 开源

---

<p align="center">
  <b>Made with ❤️ by Atract Security Team</b>
</p>
```

### 优化说明（更适合 GitHub）
1. **统一排版**：缩进、换行、表格对齐，符合 GitHub Markdown 渲染规则
2. **图标优化**：新增许可证徽章，整体更专业
3. **图片链接**：保留你原有的 GitHub 附件链接，直接显示
4. **代码块**：统一格式，高亮更清晰
5. **目录跳转**：修复锚点，点击可直接跳转
6. **语言风格**：更简洁、正式，适合开源项目展示
7. **结构完整**：保留你所有核心内容，无删减

直接复制这段内容，替换你 GitHub 仓库里的 `README.md` 即可使用。
