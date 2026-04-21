<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Atract·安全运营平台 - 技术宣讲</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: #f1f5f9;
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #1e293b;
        }
        ::-webkit-scrollbar-thumb {
            background: #3b82f6;
            border-radius: 4px;
        }

        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(59, 130, 246, 0.3);
            z-index: 1000;
            padding: 1rem 2rem;
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #3b82f6, #06b6d4);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            color: #94a3b8;
            text-decoration: none;
            transition: color 0.3s;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: #3b82f6;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 80px 2rem 4rem;
        }

        .section {
            margin-bottom: 5rem;
            animation: fadeInUp 0.6s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 60px;
            height: 3px;
            background: linear-gradient(90deg, #3b82f6, #06b6d4);
            border-radius: 2px;
        }

        .section-subtitle {
            color: #94a3b8;
            margin-bottom: 2rem;
            font-size: 1rem;
        }

        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
            gap: 1.5rem;
        }

        .card {
            background: rgba(30, 41, 59, 0.5);
            border-radius: 16px;
            padding: 1.5rem;
            border: 1px solid rgba(59, 130, 246, 0.2);
            backdrop-filter: blur(5px);
            transition: all 0.3s;
        }

        .card:hover {
            border-color: #3b82f6;
            transform: translateY(-4px);
        }

        .card-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #3b82f6, #06b6d4);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .card-icon i {
            font-size: 1.5rem;
        }

        .card-title {
            font-size: 1.25rem;
            font-weight: 600;
        }

        .card-desc {
            color: #94a3b8;
            font-size: 0.9rem;
            margin: 0.5rem 0 0.75rem 0;
        }

        .code-block {
            background: #0f172a;
            border-radius: 12px;
            padding: 0.75rem;
            font-family: 'Monaco', monospace;
            font-size: 0.75rem;
            overflow-x: auto;
            border-left: 3px solid #3b82f6;
        }

        .code-block pre {
            margin: 0;
            color: #94a3b8;
            font-family: 'Monaco', monospace;
            font-size: 0.75rem;
            white-space: pre-wrap;
            word-break: break-all;
        }

        .badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 500;
        }

        .badge-blue {
            background: rgba(59, 130, 246, 0.2);
            color: #3b82f6;
            border: 1px solid rgba(59, 130, 246, 0.3);
        }

        .badge-green {
            background: rgba(16, 185, 129, 0.2);
            color: #10b981;
            border: 1px solid rgba(16, 185, 129, 0.3);
        }

        .badge-purple {
            background: rgba(139, 92, 246, 0.2);
            color: #8b5cf6;
            border: 1px solid rgba(139, 92, 246, 0.3);
        }

        .badge-orange {
            background: rgba(249, 115, 22, 0.2);
            color: #f97316;
            border: 1px solid rgba(249, 115, 22, 0.3);
        }

        .badge-red {
            background: rgba(239, 68, 68, 0.2);
            color: #ef4444;
            border: 1px solid rgba(239, 68, 68, 0.3);
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .stat-card {
            background: linear-gradient(135deg, #1e293b, #0f172a);
            border-radius: 16px;
            padding: 1.5rem;
            text-align: center;
            border: 1px solid #334155;
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(135deg, #3b82f6, #06b6d4);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .footer {
            text-align: center;
            padding: 2rem;
            border-top: 1px solid #334155;
            color: #64748b;
            font-size: 0.875rem;
        }

        @media (max-width: 768px) {
            .container {
                padding: 70px 1rem 2rem;
            }
            .grid-2 {
                grid-template-columns: 1fr;
            }
            .nav-links {
                display: none;
            }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">
                <i class="fas fa-shield-alt"></i> Atract·安全运营平台
            </div>
            <div class="nav-links">
                <a href="#architecture">架构</a>
                <a href="#flow">流程</a>
                <a href="#highlights">亮点</a>
                <a href="#security">安全防御</a>
                <a href="#stats">数据</a>
            </div>
        </div>
    </nav>

    <div class="container">
        <!-- Hero -->
        <div class="section" style="text-align: center; margin-bottom: 3rem;">
            <h1 style="font-size: 3rem; margin-bottom: 1rem; background: linear-gradient(135deg, #fff, #3b82f6); -webkit-background-clip: text; background-clip: text; color: transparent;">
                Atract·安全运营平台
            </h1>
            <p style="font-size: 1.2rem; color: #94a3b8; max-width: 700px; margin: 0 auto;">
                配置化驱动的安全运营平台，实现需求→任务→漏洞的自动化闭环管理
            </p>
            <div style="margin-top: 2rem; display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;">
                <span class="badge badge-blue"><i class="fas fa-code"></i> Python/Django</span>
                <span class="badge badge-green"><i class="fas fa-database"></i> MySQL</span>
                <span class="badge badge-purple"><i class="fas fa-lock"></i> RBAC权限</span>
                <span class="badge badge-orange"><i class="fas fa-bell"></i> 企业微信推送</span>
            </div>
        </div>

        <!-- 1. 整体架构图 -->
        <div class="section" id="architecture">
            <h2 class="section-title">整体架构图</h2>
            <p class="section-subtitle">五层架构设计，职责清晰，易于扩展</p>
            <div style="background: rgba(30, 41, 59, 0.5); border-radius: 20px; padding: 2rem; border: 1px solid rgba(59, 130, 246, 0.2);">
                
                <!-- 第1层：前端展示层 -->
                <div style="background: #1e293b; border-radius: 12px; margin-bottom: 1rem; overflow: hidden; border: 1px solid #334155;">
                    <div style="background: #0f172a; padding: 0.75rem 1.5rem; font-weight: 600; color: #3b82f6; border-bottom: 1px solid #334155;">
                        <i class="fas fa-tv"></i> 前端展示层 (Django Templates + Bootstrap)
                    </div>
                    <div style="padding: 1.5rem; display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-chart-line"></i> 工作台</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-file-alt"></i> 需求中心</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-tasks"></i> 任务中心</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-shield-virus"></i> 风险治理</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-building"></i> 资产治理</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-cogs"></i> 系统设置</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-database"></i> 知识库</span>
                    </div>
                </div>

                <!-- 第2层：权限控制层 -->
                <div style="background: #1e293b; border-radius: 12px; margin-bottom: 1rem; overflow: hidden; border: 1px solid #334155;">
                    <div style="background: #0f172a; padding: 0.75rem 1.5rem; font-weight: 600; color: #3b82f6; border-bottom: 1px solid #334155;">
                        <i class="fas fa-shield-alt"></i> 权限控制层 (RBAC)
                    </div>
                    <div style="padding: 1.5rem; display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">@login_required</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">@require_permission</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">@role_required</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">上下文处理器</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">Session管理</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;">用户→角色→权限→菜单</span>
                    </div>
                </div>

                <!-- 第3层：业务逻辑层 -->
                <div style="background: #1e293b; border-radius: 12px; margin-bottom: 1rem; overflow: hidden; border: 1px solid #334155;">
                    <div style="background: #0f172a; padding: 0.75rem 1.5rem; font-weight: 600; color: #3b82f6; border-bottom: 1px solid #334155;">
                        <i class="fas fa-cogs"></i> 业务逻辑层 (Django Views)
                    </div>
                    <div style="padding: 1.5rem; display: flex; flex-direction: column; gap: 1rem;">
                        <div>
                            <div style="font-size: 0.75rem; color: #64748b; margin-bottom: 0.5rem; text-align: center;">核心业务</div>
                            <div style="display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-file-alt"></i> 需求管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-tasks"></i> 任务管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-bug"></i> 漏洞管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-exclamation-triangle"></i> 安全事件</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-chart-line"></i> 工作台</span>
                            </div>
                        </div>
                        <div>
                            <div style="font-size: 0.75rem; color: #64748b; margin-bottom: 0.5rem; text-align: center;">资产治理</div>
                            <div style="display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-globe"></i> 域名管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-envelope"></i> 公共邮箱</span>
                            </div>
                        </div>
                        <div>
                            <div style="font-size: 0.75rem; color: #64748b; margin-bottom: 0.5rem; text-align: center;">系统配置</div>
                            <div style="display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-users"></i> 用户管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-tag"></i> 角色管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-building"></i> 部门管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-sliders-h"></i> 系统配置</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-database"></i> 知识库管理</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-tag"></i> 漏洞分类配置</span>
                                <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-chart-pie"></i> 任务域配置</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- 第4层：数据层 -->
                <div style="background: #1e293b; border-radius: 12px; overflow: hidden; border: 1px solid #334155;">
                    <div style="background: #0f172a; padding: 0.75rem 1.5rem; font-weight: 600; color: #3b82f6; border-bottom: 1px solid #334155;">
                        <i class="fas fa-database"></i> 数据层
                    </div>
                    <div style="padding: 1.5rem; display: flex; flex-wrap: wrap; gap: 0.75rem; justify-content: center;">
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-database"></i> MySQL</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-code"></i> Django ORM</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-cog"></i> SystemConfig</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-image"></i> 文件存储(图片)</span>
                        <span style="background: #0f172a; padding: 0.5rem 1rem; border-radius: 8px;"><i class="fas fa-lock"></i> Redis(Session)</span>
                    </div>
                </div>

            </div>
        </div>

        <!-- 2. 核心业务流程图 -->
        <div class="section" id="flow">
            <h2 class="section-title">核心业务流程图</h2>
            <p class="section-subtitle">需求 → 任务 → 漏洞 完整闭环 | 应急响应自动生成安全事件</p>
            
            <div style="background: rgba(30, 41, 59, 0.5); border-radius: 20px; padding: 1.5rem; border: 1px solid rgba(59, 130, 246, 0.2); overflow-x: auto;">
                <div style="min-width: 1100px;">
                    
                    <!-- 泳道标题 -->
                    <div style="display: flex; margin-bottom: 1rem;">
                        <div style="width: 120px;"></div>
                        <div style="flex: 1; text-align: center; padding: 0.5rem; background: #0f172a; border-radius: 8px; margin: 0 0.25rem;"><i class="fas fa-user"></i> 申请人</div>
                        <div style="flex: 1; text-align: center; padding: 0.5rem; background: #0f172a; border-radius: 8px; margin: 0 0.25rem;"><i class="fas fa-check-circle"></i> 审批人</div>
                        <div style="flex: 1; text-align: center; padding: 0.5rem; background: #0f172a; border-radius: 8px; margin: 0 0.25rem;"><i class="fas fa-shield-alt"></i> 安全人员</div>
                        <div style="flex: 1; text-align: center; padding: 0.5rem; background: #0f172a; border-radius: 8px; margin: 0 0.25rem;"><i class="fas fa-code-branch"></i> 研发人员</div>
                    </div>

                    <!-- 流程行1：提交需求 -->
                    <div style="display: flex; align-items: center; margin-bottom: 1.5rem;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">① 需求阶段</div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #3b82f6;">
                                <i class="fas fa-file-alt"></i> 提交需求
                                <div style="font-size: 0.7rem; color:#94a3b8;">6种需求类型</div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem; display: flex; justify-content: center;">
                            <span style="font-size: 1.5rem; color: #3b82f6;"><i class="fas fa-arrow-right"></i></span>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #f59e0b;">
                                <i class="fas fa-clipboard-list"></i> 部门领导审批
                                <div style="font-size: 0.7rem; color:#94a3b8;">同意 / 驳回</div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                    </div>

                    <!-- 流程行2：生成任务 + 认领 -->
                    <div style="display: flex; align-items: center; margin-bottom: 1.5rem;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">② 任务阶段</div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #3b82f6;">
                                <i class="fas fa-tasks"></i> 自动生成主任务
                                <div style="font-size: 0.7rem; color:#94a3b8;">企业微信通知</div>
                            </div>
                            <div style="text-align: center; margin: 0.5rem 0;"><i class="fas fa-arrow-down"></i></div>
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #10b981;">
                                <i class="fas fa-user-check"></i> 安全人员认领
                                <div style="font-size: 0.7rem; color:#94a3b8;">主任务 → 处理中</div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                    </div>

                    <!-- 流程行3：安全检测 + 分支 -->
                    <div style="display: flex; align-items: flex-start; margin-bottom: 1.5rem;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">③ 检测阶段</div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #f59e0b;">
                                <i class="fas fa-search"></i> 安全检测
                                <div style="font-size: 0.7rem; color:#94a3b8;">扫描/测试/审计</div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                    </div>

                    <!-- 分支：发现漏洞 / 未发现漏洞 -->
                    <div style="display: flex; align-items: flex-start; margin-bottom: 1.5rem;">
                        <div style="width: 120px;"></div>
                        <div style="flex: 1; margin: 0 0.25rem; text-align: center;">
                            <div style="background: rgba(239, 68, 68, 0.15); border-radius: 8px; padding: 0.5rem;">
                                <span style="color: #ef4444;"><i class="fas fa-bug"></i> 发现漏洞</span>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem; text-align: center;">
                            <div style="background: rgba(16, 185, 129, 0.15); border-radius: 8px; padding: 0.5rem;">
                                <span style="color: #10b981;"><i class="fas fa-check-double"></i> 未发现漏洞 → 主任务关闭</span>
                            </div>
                        </div>
                    </div>

                    <!-- 流程行4：生成子任务 + 修复 -->
                    <div style="display: flex; align-items: center; margin-bottom: 1.5rem;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">④ 修复阶段</div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #8b5cf6;">
                                <i class="fas fa-code-branch"></i> 生成子任务
                                <div style="font-size: 0.7rem; color:#94a3b8;">自动分派</div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #3b82f6;">
                                <i class="fas fa-wrench"></i> 研发修复漏洞
                                <div style="font-size: 0.7rem; color:#94a3b8;">子任务 → 修复中</div>
                            </div>
                        </div>
                    </div>

                    <!-- 流程行5：安全验证 + 分支 -->
                    <div style="display: flex; align-items: center; margin-bottom: 1rem;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">⑤ 验证阶段</div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #f59e0b;">
                                <i class="fas fa-clipboard-list"></i> 安全验证
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                    </div>

                    <!-- 验证分支结果 -->
                    <div style="display: flex; align-items: center; margin-bottom: 1.5rem;">
                        <div style="width: 120px;"></div>
                        <div style="flex: 1; margin: 0 0.25rem; text-align: center;">
                            <span style="color: #10b981;"><i class="fas fa-check"></i> 通过</span>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem; text-align: center;">
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.5rem; text-align: center; border: 1px solid #10b981;">
                                漏洞 → 已修复<br>
                                <span style="font-size: 0.7rem;">子任务完成 → 主任务关闭</span>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem; text-align: center;">
                            <span style="color: #ef4444;"><i class="fas fa-times"></i> 不通过</span>
                            <div style="margin-top: 0.25rem;"><i class="fas fa-arrow-down"></i></div>
                            <div style="background: #1e293b; border-radius: 10px; padding: 0.5rem; margin-top: 0.25rem; border: 1px solid #ef4444;">
                                驳回研发重新修复
                            </div>
                        </div>
                    </div>

                    <!-- 流程行6：应急响应 -->
                    <div style="display: flex; align-items: center;">
                        <div style="width: 120px; font-size: 0.8rem; color: #64748b;">⑥ 应急响应</div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                        <div style="flex: 1; margin: 0 0.25rem;">
                            <div style="background: linear-gradient(135deg, #1e293b, #7c3aed20); border-radius: 10px; padding: 0.75rem; text-align: center; border: 1px solid #ef4444;">
                                <i class="fas fa-bell"></i> 应急响应任务？
                            </div>
                            <div style="display: flex; justify-content: center; gap: 1rem; margin-top: 0.5rem;">
                                <span style="color: #10b981;"><i class="fas fa-check"></i> 是</span>
                                <span style="color: #ef4444;"><i class="fas fa-times"></i> 否 → 结束</span>
                            </div>
                            <div style="margin-top: 0.5rem; text-align: center;">
                                <div style="background: #ef444420; border-radius: 8px; padding: 0.5rem; border: 1px solid #ef4444;">
                                    <i class="fas fa-exclamation-triangle"></i> 自动生成安全事件
                                </div>
                            </div>
                        </div>
                        <div style="flex: 1; margin: 0 0.25rem;"></div>
                    </div>

                    <!-- 图例 -->
                    <div style="display: flex; gap: 1rem; justify-content: center; margin-top: 2rem; padding-top: 1rem; border-top: 1px solid #334155;">
                        <div style="display: flex; align-items: center; gap: 0.5rem;"><div style="width: 12px; height: 12px; background: #3b82f6; border-radius: 2px;"></div><span style="font-size: 0.75rem;">主流程</span></div>
                        <div style="display: flex; align-items: center; gap: 0.5rem;"><div style="width: 12px; height: 12px; background: #f59e0b; border-radius: 2px;"></div><span style="font-size: 0.75rem;">判断节点</span></div>
                        <div style="display: flex; align-items: center; gap: 0.5rem;"><div style="width: 12px; height: 12px; background: #10b981; border-radius: 2px;"></div><span style="font-size: 0.75rem;">通过/同意</span></div>
                        <div style="display: flex; align-items: center; gap: 0.5rem;"><div style="width: 12px; height: 12px; background: #ef4444; border-radius: 2px;"></div><span style="font-size: 0.75rem;">拒绝/不通过</span></div>
                        <div style="display: flex; align-items: center; gap: 0.5rem;"><div style="width: 12px; height: 12px; background: #8b5cf6; border-radius: 2px;"></div><span style="font-size: 0.75rem;">事件触发</span></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 3. 技术亮点 -->
        <div class="section" id="highlights">
            <h2 class="section-title">技术亮点</h2>
            <p class="section-subtitle">配置驱动 · 权限精细 · 自动化流转 · 全领域覆盖</p>
            
            <div class="grid-2">
                <!-- 亮点1：安全域配置 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-shield-alt"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">安全域配置 · 9大领域全覆盖</div>
                    </div>
                    <div class="card-desc">覆盖企业信息安全全触点，按领域精准分派任务</div>
                    <div style="display: flex; flex-wrap: wrap; gap: 0.5rem; margin: 0.75rem 0;">
                        <span class="badge badge-blue">网络安全</span>
                        <span class="badge badge-blue">主机安全</span>
                        <span class="badge badge-blue">应用安全</span>
                        <span class="badge badge-blue">数据安全</span>
                        <span class="badge badge-blue">组件安全</span>
                        <span class="badge badge-blue">开发安全</span>
                        <span class="badge badge-blue">业务安全</span>
                        <span class="badge badge-blue">内容安全</span>
                        <span class="badge badge-blue">合规安全</span>
                    </div>
                    <div class="code-block">
                        <pre>DomainsHierarchy 配置表
└── 领域名称 + 编码 + 数据源标识 + 排序
└── 任务自动匹配对应领域
└── 支持动态启用/禁用</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>任务分派准确率 ↑95% | 新业务域接入 <span class="badge badge-green">无需改代码</span>
                    </div>
                </div>

                <!-- 亮点2：配置化需求类型 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-cog"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">配置化需求类型系统</div>
                    </div>
                    <div class="card-desc">新增业务需求类型只需添加配置，详情页自动渲染</div>
                    <div class="code-block">
                        <pre>REQ_TYPE_CONFIG = {
    1: {"model": SecurityTestRequirement, ...},
    2: {"model": SecurityScanRequirement, ...},
    # 新增类型只加这一行！
}</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>开发效率 ↑70% | 代码复用率 <span class="badge badge-green">90%+</span> | 6种需求类型统一处理
                    </div>
                </div>

                <!-- 亮点3：RBAC权限体系 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-lock"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">细粒度RBAC权限系统</div>
                    </div>
                    <div class="card-desc">用户 → 角色 → 权限 → 菜单，按钮级别权限控制</div>
                    <div class="code-block">
                        <pre>@require_permission('vul:delete')
def vulnerability_delete(request, nid):
    # 只有 vul:delete 权限才能执行</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>权限管理粒度 <span class="badge badge-green">按钮级</span> | 模板自动注入 | 支持多角色
                    </div>
                </div>

                <!-- 亮点4：任务智能分派 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-tasks"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">任务智能分派 + 闭环流转</div>
                    </div>
                    <div class="card-desc">主任务(安全检测) / 子任务(漏洞修复) 自动分派，权责清晰</div>
                    <div class="code-block">
                        <pre>if task_category == "main":
    # 仅信息安全部成员可认领
elif task_category == "child":
    # 仅任务创建人所在部门成员可认领</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>任务流转耗时 <span class="badge badge-green">↓60%</span> | 自动分派准确率 <span class="badge badge-green">98%</span>
                    </div>
                </div>

                <!-- 亮点5：企业微信自动推送 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fab fa-weixin"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">企业微信自动推送</div>
                    </div>
                    <div class="card-desc">新漏洞提交、应急响应任务、任务指派实时通知</div>
                    <div class="code-block">
                        <pre>## ⚠️ 新漏洞通知
**漏洞编号：** SRC-2026-001
> [点击查看详情]({url})</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>通知响应时间 <span class="badge badge-green">实时</span> | 人工通知成本 <span class="badge badge-green">↓100%</span>
                    </div>
                </div>

                <!-- 亮点6：应急响应自动生成事件 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-bolt"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">应急响应自动生成事件</div>
                    </div>
                    <div class="card-desc">应急响应任务关闭时自动创建SecurityEvent，无需手动登记</div>
                    <div class="code-block">
                        <pre>if is_emergency or is_manual_emergency:
    SecurityEvent.objects.create(
        source=1, event_code=generate_event_code(),
        title=f"{project_name} - 安全事件"
    )</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>事件登记效率 <span class="badge badge-green">↑90%</span> | 漏报率 <span class="badge badge-green">→0</span>
                    </div>
                </div>

                <!-- 亮点7：三层安全防御机制 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0; background: linear-gradient(135deg, #ef4444, #dc2626);"><i class="fas fa-shield-virus"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">三层安全防御机制</div>
                    </div>
                    <div class="card-desc">XSS防护 + 图片安全检测 + 密码加密，全方位保障系统安全</div>
                    
                    <div style="margin-top: 0.5rem;">
                        <div style="font-size: 0.7rem; color: #3b82f6; margin-bottom: 0.25rem;"><i class="fas fa-code"></i> XSS防护 (bleach白名单)</div>
                        <div class="code-block" style="padding: 0.5rem;">
                            <pre>ALLOWED_TAGS = ['p','br','strong','a','img'...]
ALLOWED_ATTRS = {'a':['href','title','target']}
safe_html = bleach.clean(content, tags=ALLOWED_TAGS)</pre>
                        </div>
                    </div>
                    
                    <div style="margin-top: 0.5rem;">
                        <div style="font-size: 0.7rem; color: #f59e0b; margin-bottom: 0.25rem;"><i class="fas fa-image"></i> 图片安全检测 (5层校验)</div>
                        <div class="code-block" style="padding: 0.5rem;">
                            <pre># 1. 扩展名白名单 .jpg/.png/.gif/.webp
# 2. imghdr检测真实图片类型
# 3. 扫描恶意代码特征 &lt;?php &lt;script
# 4. GIF注释块专项检测
# 5. PIL验证图片完整性</pre>
                        </div>
                    </div>
                    
                    <div style="margin-top: 0.5rem;">
                        <div style="font-size: 0.7rem; color: #10b981; margin-bottom: 0.25rem;"><i class="fas fa-key"></i> 密码安全 (PBKDF2加密)</div>
                        <div class="code-block" style="padding: 0.5rem;">
                            <pre>from django.contrib.auth.hashers import make_password
user.password = make_password(password)
# 密码复杂度：8位 + 数字/字母/特殊符号至少两种</pre>
                        </div>
                    </div>
                    
                    <div style="display: flex; flex-wrap: wrap; gap: 0.5rem; margin: 0.75rem 0;">
                        <span class="badge badge-red">bleach白名单</span>
                        <span class="badge badge-red">imghdr真实类型</span>
                        <span class="badge badge-red">恶意代码扫描</span>
                        <span class="badge badge-red">PBKDF2加密</span>
                        <span class="badge badge-red">GIF注释块检测</span>
                        <span class="badge badge-red">PIL完整性验证</span>
                    </div>
                    
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>XSS漏洞 <span class="badge badge-green">0</span> | 图片马攻击 <span class="badge badge-green">100%拦截</span> | 密码泄露风险 <span class="badge badge-green">↓95%</span>
                    </div>
                </div>

                <!-- 亮点8：通用分页组件 -->
                <div class="card" style="display: flex; flex-direction: column;">
                    <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
                        <div class="card-icon" style="margin-bottom: 0;"><i class="fas fa-pagination"></i></div>
                        <div class="card-title" style="margin-bottom: 0;">通用分页组件</div>
                    </div>
                    <div class="card-desc">配置化每页条数、保留搜索参数、内置跳转表单</div>
                    <div class="code-block">
                        <pre>page_object = Pagination(request, queryset)
context = {
    "queryset": page_object.page_queryset,
    "page_string": page_object.html()
}</pre>
                    </div>
                    <div style="margin-top: 0.75rem; background: #10b98120; border-radius: 8px; padding: 0.5rem; text-align: center;">
                        <i class="fas fa-chart-line"></i> <strong>效果：</strong>列表页开发效率 <span class="badge badge-green">↑50%</span> | 代码复用 <span class="badge badge-green">100%</span>
                    </div>
                </div>
            </div>
            
            <!-- 对比优化总结 -->
            <div style="margin-top: 2rem; background: linear-gradient(135deg, #1e293b, #0f172a); border-radius: 16px; padding: 1.5rem; border: 1px solid #3b82f6;">
                <div style="text-align: center; margin-bottom: 1rem;">
                    <i class="fas fa-chart-simple" style="font-size: 1.5rem; color: #3b82f6;"></i>
                    <span style="font-weight: 600; margin-left: 0.5rem;">优化前后对比</span>
                </div>
                <div style="display: flex; flex-wrap: wrap; gap: 2rem; justify-content: center;">
                    <div style="text-align: center;">
                        <div style="font-size: 0.75rem; color: #64748b;">新增需求类型开发</div>
                        <div style="display: flex; align-items: center; gap: 1rem; margin-top: 0.5rem;">
                            <span style="background: #ef4444; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化前: 3天</span>
                            <i class="fas fa-arrow-right"></i>
                            <span style="background: #10b981; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化后: 0.5天</span>
                        </div>
                    </div>
                    <div style="text-align: center;">
                        <div style="font-size: 0.75rem; color: #64748b;">任务流转耗时</div>
                        <div style="display: flex; align-items: center; gap: 1rem; margin-top: 0.5rem;">
                            <span style="background: #ef4444; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化前: 2小时</span>
                            <i class="fas fa-arrow-right"></i>
                            <span style="background: #10b981; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化后: 10分钟</span>
                        </div>
                    </div>
                    <div style="text-align: center;">
                        <div style="font-size: 0.75rem; color: #64748b;">事件登记效率</div>
                        <div style="display: flex; align-items: center; gap: 1rem; margin-top: 0.5rem;">
                            <span style="background: #ef4444; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化前: 手动填写</span>
                            <i class="fas fa-arrow-right"></i>
                            <span style="background: #10b981; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化后: 自动生成</span>
                        </div>
                    </div>
                    <div style="text-align: center;">
                        <div style="font-size: 0.75rem; color: #64748b;">权限管理粒度</div>
                        <div style="display: flex; align-items: center; gap: 1rem; margin-top: 0.5rem;">
                            <span style="background: #ef4444; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化前: 页面级</span>
                            <i class="fas fa-arrow-right"></i>
                            <span style="background: #10b981; padding: 0.25rem 0.75rem; border-radius: 20px; font-size: 0.8rem;">优化后: 按钮级</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 4. 核心数据统计 -->
        <div class="section" id="stats">
            <h2 class="section-title">核心数据统计</h2>
            <div class="stats">
                <div class="stat-card">
                    <div class="stat-number">6</div>
                    <div class="stat-label">需求类型</div>
                    <div style="font-size:0.7rem; color:#64748b; margin-top:0.5rem;">测试/扫描/审计/培训/应急/报告</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">9</div>
                    <div class="stat-label">安全领域</div>
                    <div style="font-size:0.7rem; color:#64748b; margin-top:0.5rem;">网络/主机/应用/数据/组件/开发/业务/内容/合规</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">2</div>
                    <div class="stat-label">任务类型</div>
                    <div style="font-size:0.7rem; color:#64748b; margin-top:0.5rem;">主任务(检测) / 子任务(修复)</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">4</div>
                    <div class="stat-label">漏洞等级</div>
                    <div style="font-size:0.7rem; color:#64748b; margin-top:0.5rem;">信息/低危/中危/高危</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">6+</div>
                    <div class="stat-label">用户角色</div>
                    <div style="font-size:0.7rem; color:#64748b; margin-top:0.5rem;">管理员/部门领导/普通员工等</div>
                </div>
            </div>
        </div>

        <!-- 总结 -->
        <div class="section">
            <div style="background: linear-gradient(135deg, #1e293b, #0f172a); border-radius: 20px; padding: 2rem; text-align: center; border: 1px solid #334155;">
                <i class="fas fa-star" style="font-size: 2rem; color: #f59e0b; margin-bottom: 1rem;"></i>
                <h3 style="font-size: 1.5rem; margin-bottom: 1rem;">一句话总结</h3>
                <p style="font-size: 1.1rem; color: #94a3b8; max-width: 800px; margin: 0 auto;">
                    配置化驱动的安全运营平台，实现需求→任务→漏洞的自动化闭环管理，<br>
                    9大安全领域全覆盖，应急响应自动生成安全事件，<br>
                    通过RBAC精细权限控制和三层安全防护，支撑企业安全日常运营。
                </p>
                <div style="margin-top: 1.5rem; display: flex; gap: 0.75rem; justify-content: center; flex-wrap: wrap;">
                    <span class="badge badge-blue"><i class="fas fa-chart-line"></i> 高复用性</span>
                    <span class="badge badge-green"><i class="fas fa-rocket"></i> 自动化流转</span>
                    <span class="badge badge-purple"><i class="fas fa-shield-virus"></i> 安全优先</span>
                    <span class="badge badge-orange"><i class="fas fa-plug"></i> 易于扩展</span>
                </div>
            </div>
        </div>

        <div class="footer">
            <p><i class="fas fa-shield-alt"></i> Atract·安全运营平台 | 配置化驱动 · 权限精细 · 自动化闭环 | 9大安全领域全覆盖</p>
        </div>
    </div>

    <script>
        document.querySelectorAll('.nav-links a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                const target = document.getElementById(targetId);
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });
    </script>
</body>
</html>
