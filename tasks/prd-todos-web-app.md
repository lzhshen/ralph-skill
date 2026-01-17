# PRD: Todos Web 应用

## Introduction

创建一个简洁的个人任务管理 Web 应用，帮助用户追踪日常待办事项。应用使用 React + TypeScript 构建，数据存储在浏览器 LocalStorage 中，无需后端服务器或用户认证。专注于核心功能：创建、编辑、删除和标记任务完成。

## Goals

- 提供简单直观的任务管理界面
- 支持任务的完整 CRUD 操作（创建、读取、更新、删除）
- 使用 LocalStorage 实现数据持久化，刷新页面后数据不丢失
- 响应式设计，支持桌面和移动设备
- 零配置启动，无需后端依赖

## User Stories

### US-001: 项目初始化
**Description:** 作为开发者，我需要搭建 React + TypeScript 项目基础结构，以便后续功能开发。

**Acceptance Criteria:**
- [ ] 使用 Vite 创建 React + TypeScript 项目
- [ ] 配置基本的项目结构（components, hooks, types, utils 目录）
- [ ] 添加基础样式重置（CSS reset）
- [ ] 项目可以正常启动运行（npm run dev）
- [ ] TypeScript 类型检查通过

---

### US-002: 定义 Todo 数据类型
**Description:** 作为开发者，我需要定义 Todo 的数据结构，以便在整个应用中保持类型一致性。

**Acceptance Criteria:**
- [ ] 创建 Todo 接口类型，包含字段：id (string), title (string), completed (boolean), createdAt (number)
- [ ] 类型定义文件位于 `src/types/todo.ts`
- [ ] TypeScript 类型检查通过

---

### US-003: 实现 LocalStorage 持久化
**Description:** 作为用户，我希望刷新页面后任务列表仍然保留，这样我不会丢失数据。

**Acceptance Criteria:**
- [ ] 创建 useLocalStorage 自定义 Hook
- [ ] 应用启动时从 LocalStorage 读取已保存的任务
- [ ] 任务变更时自动保存到 LocalStorage
- [ ] 处理 LocalStorage 读取失败的情况（返回空数组）
- [ ] TypeScript 类型检查通过

---

### US-004: 显示任务列表
**Description:** 作为用户，我希望看到所有待办任务的列表，以便了解需要完成的工作。

**Acceptance Criteria:**
- [ ] 创建 TodoList 组件，显示所有任务
- [ ] 每个任务显示标题和完成状态
- [ ] 已完成的任务有视觉区分（如删除线样式）
- [ ] 空列表时显示友好提示（如"暂无任务"）
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-005: 添加新任务
**Description:** 作为用户，我希望能够添加新的待办任务，这样我可以记录需要完成的事项。

**Acceptance Criteria:**
- [ ] 创建 TodoInput 组件，包含输入框和添加按钮
- [ ] 输入框支持回车键提交
- [ ] 提交后输入框自动清空
- [ ] 空内容不允许提交（去除首尾空格后判断）
- [ ] 新任务默认为未完成状态
- [ ] 新任务自动生成唯一 ID 和创建时间
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-006: 标记任务完成/未完成
**Description:** 作为用户，我希望能够切换任务的完成状态，这样我可以追踪进度。

**Acceptance Criteria:**
- [ ] 每个任务项有复选框或可点击区域
- [ ] 点击后切换任务的 completed 状态
- [ ] 状态变更立即反映在 UI 上
- [ ] 状态变更自动保存到 LocalStorage
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-007: 删除任务
**Description:** 作为用户，我希望能够删除不需要的任务，保持列表整洁。

**Acceptance Criteria:**
- [ ] 每个任务项有删除按钮
- [ ] 点击删除按钮后任务从列表中移除
- [ ] 删除操作立即反映在 UI 上
- [ ] 删除后自动更新 LocalStorage
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-008: 编辑任务标题
**Description:** 作为用户，我希望能够修改任务标题，以便更正错误或更新内容。

**Acceptance Criteria:**
- [ ] 双击任务标题进入编辑模式
- [ ] 编辑模式显示输入框，预填当前标题
- [ ] 按回车键或失去焦点时保存修改
- [ ] 按 Escape 键取消编辑，恢复原标题
- [ ] 空标题不允许保存
- [ ] 修改后自动更新 LocalStorage
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-009: 显示任务统计
**Description:** 作为用户，我希望看到任务完成情况的统计，了解整体进度。

**Acceptance Criteria:**
- [ ] 显示总任务数和已完成任务数（如 "3/5 已完成"）
- [ ] 统计数据实时更新
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

---

### US-010: 响应式布局
**Description:** 作为用户，我希望在手机上也能正常使用应用。

**Acceptance Criteria:**
- [ ] 桌面端布局合理，最大宽度限制（如 600px）
- [ ] 移动端（< 480px）布局自适应
- [ ] 按钮和输入框尺寸适合触摸操作
- [ ] TypeScript 类型检查通过
- [ ] Verify in browser using dev-browser skill

## Functional Requirements

- **FR-1:** 应用使用 React 18+ 和 TypeScript 构建
- **FR-2:** 应用使用 Vite 作为构建工具
- **FR-3:** Todo 数据结构包含：id (string), title (string), completed (boolean), createdAt (number)
- **FR-4:** 所有数据存储在 LocalStorage，key 为 `todos`
- **FR-5:** 用户可以通过输入框添加新任务，回车或点击按钮提交
- **FR-6:** 用户可以点击复选框切换任务完成状态
- **FR-7:** 用户可以点击删除按钮移除任务
- **FR-8:** 用户可以双击任务标题进入编辑模式
- **FR-9:** 应用显示任务完成统计信息
- **FR-10:** 应用支持响应式布局

## Non-Goals

- 不包含用户认证/登录功能
- 不包含后端 API 或数据库
- 不包含多设备同步
- 不包含任务分类或标签功能
- 不包含任务优先级
- 不包含截止日期或提醒功能
- 不包含拖拽排序
- 不包含任务搜索或过滤
- 不包含批量操作（全选、批量删除）
- 不包含暗黑模式

## Design Considerations

### UI 布局
```
┌─────────────────────────────────────┐
│           Todo App                  │
├─────────────────────────────────────┤
│  [输入框__________________] [添加]   │
├─────────────────────────────────────┤
│  ☐ 买牛奶                    [删除] │
│  ☑ 写周报（删除线）           [删除] │
│  ☐ 打电话给妈妈              [删除] │
├─────────────────────────────────────┤
│           2/3 已完成                │
└─────────────────────────────────────┘
```

### 样式建议
- 使用简洁的现代风格
- 主色调：蓝色系（#3b82f6）
- 背景色：浅灰（#f3f4f6）
- 卡片背景：白色
- 已完成任务：灰色文字 + 删除线

## Technical Considerations

### 项目结构
```
src/
├── components/
│   ├── TodoInput.tsx      # 输入框组件
│   ├── TodoList.tsx       # 任务列表组件
│   ├── TodoItem.tsx       # 单个任务组件
│   └── TodoStats.tsx      # 统计信息组件
├── hooks/
│   └── useLocalStorage.ts # LocalStorage Hook
├── types/
│   └── todo.ts            # 类型定义
├── App.tsx                # 主应用组件
├── App.css                # 样式文件
├── main.tsx               # 入口文件
└── index.css              # 全局样式
```

### 依赖
- React 18+
- TypeScript 5+
- Vite（构建工具）
- 无需其他第三方 UI 库

### LocalStorage 数据格式
```json
{
  "todos": [
    {
      "id": "uuid-1",
      "title": "买牛奶",
      "completed": false,
      "createdAt": 1699999999999
    }
  ]
}
```

## Success Metrics

- 用户可以在 3 秒内完成添加一个新任务
- 所有操作响应时间 < 100ms
- 页面刷新后数据 100% 保留
- 应用在主流浏览器（Chrome, Firefox, Safari, Edge）正常运行

## Open Questions

- 是否需要确认删除对话框？（当前方案：直接删除）
- 任务列表是否需要排序？（当前方案：按创建时间倒序，新任务在上）
- 是否需要清除所有已完成任务的功能？（当前方案：不包含）
