# Ollama 项目概述 - 2026-03-19

## 项目基本信息
- 项目名称：视频采集与高性能管理系统
- 项目位置：~/Documents/ollama
- 技术栈：Go + Gin + MySQL 8.0 + Redis + Docker Compose

## 核心架构
- 后端：Go语言，使用Gin框架
- 数据库：MySQL 8.0，utf8mb4字符集
- 缓存：Redis，用于热点缓存、限流和分布式锁
- 部署：Docker Compose四容器编排（mysql-node, redis-node, api-service, frontend-node）

## 主要功能模块
1. 视频采集任务管理（支持HTTP、RSS、M3U8等多种源）
2. 视频内容管理（分类、标签、审核流程）
3. 后台用户权限管理（RBAC模型）
4. API客户端授权管理
5. 采集任务队列与异步处理
6. 审计日志系统

## 技术特色
- 高性能缓存策略（视频详情、分类列表缓存）
- 分布式队列处理采集任务
- 自动分类匹配算法
- 互动统计与防刷机制
- 优雅启停和健康检查

## 数据库表结构
- categories: 视频分类表（支持无限级分类）
- videos: 视频核心信息表
- tags: 视频标签表
- video_tags: 视频与标签关联表
- api_clients: API客户端授权表
- admin_users: 后台管理员表
- admin_roles: 后台角色表
- collect_tasks: 采集任务表
- collect_task_logs: 采集任务日志表
- stats: 视频统计表

## 关键服务
- VideoService: 视频业务逻辑处理
- CollectService: 采集任务处理
- 支持XML/RSS采集源解析
- 支持MacCMS兼容接口