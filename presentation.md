---
marp: true
size: 16:9
theme: am_blue
paginate: true
headingDivider: [2,3]
footer: \ *AI辅助编程* *GitHub Copilot* *实战经验*
---

# 码上达人 AI辅助编程讲座

###### 提升编程效率与质量的现代方法

<!-- _class: cover_e -->
<!-- _header: "" --> 
<!-- _footer: "" --> 
<!-- _paginate: "" --> 

VSCode/Jetbrains + GitHub Copilot
王思宇
2025年5月9日

## 目录

<!-- _class: cols2_ol_ci fglass toc_a  -->
<!-- _footer: "" --> 
<!-- _header: "CONTENTS" --> 
<!-- _paginate: "" -->

- [环境配置与代码编辑器介绍](#3)
- [为什么要重视AI辅助编程](#5)
- [AI编程方法论](#7)
- [AI编程工具对比与选择](#10)
- [如何选择AI模型](#14)
- [GitHub Copilot功能详解](#15)
- [项目实战经验分享](#16)
- [拓展内容：MCP服务器](#22)

## 1. 环境配置与代码编辑器介绍

<!-- _class: trans navbar -->
<!-- _header: \ ***@AI辅助编程*** **环境配置** *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* *实战经验* -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 1. 环境配置与代码编辑器介绍

<!-- _class: cols-2-73 navbar -->
<!-- _header: \ ***@AI辅助编程*** **环境配置** *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* *实战经验* -->
<div class=ldiv>

#### 环境配置
- 代码编辑器安装 (有其一就行，推荐VSCode)
  - Visual Studio Code
  - JetBrains系列IDE
- GitHub Copilot插件安装
- git版本控制工具安装

```powershell
# 一键安装Vscode, git以及C/C++, python, js运行环境！cmd中输入：
winget install chocolatey
choco install vscode git python3 mingw nodejs
```

</div>

<div class="rdiv">

#### 代码编辑器介绍
- VSCode: 超高级记事本，非常通用
- Jetbrains: IDE(集成开发环境)
- 其他编辑器：Vim, Neovim, Sublime Text, ...

</div>


## 2. 为什么要重视AI辅助编程

<!-- _class: trans navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* **重要意义** *方法论* *工具对比* *模型选择* *Copilot功能* *实战经验* -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 2. 为什么要重视AI辅助编程

<!-- _class: fixedtitleA navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* **重要意义** *方法论* *工具对比* *模型选择* *Copilot功能* *实战经验* -->


<!-- _class: cols-2-64 -->
<div class=ldiv>

#### 斯坦福2025 AI Index报告

- AI已成为现代软件开发不可或缺的一部分
- 模型性能持续迭代：
  - 在一些设置中，语言模型代理甚至在有限时间预算内**超越了人类编程任务表现**，且在某些特定任务（如编写Triton内核）上**已与人类专家水平相当**，同时能更快地交付结果且成本更低。
  - 在以MMMU、GPQA、SWE-bench等为代表的基准测试上的表现**持续大幅进步**。
</div>

<div class=rdiv>

![h:500](pics/stanford.png)

</div>

## 2. 为什么要重视AI辅助编程

<!-- _class: navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* **重要意义** *方法论* *工具对比* *模型选择* *Copilot功能* *实战经验* -->

- 在可预见的未来，AI性能会不断提升，学会用AI辅助编程会是一项必需技能，即使对专业与计算机相关专业无关的人们而言也是如此。
- **自动化思维**：用ai辅助编程是你能充分发挥电脑能力，自动化很多日常事务的突破口！

|需求/场景|方法|语言|
|---|---|---|
|需要给一些图片加水印|写了个批量给图片加水印的脚本|python|
|背单词；词汇表是pdf表格，想要提取成文字形式|写了pdf table -> csv的脚本|python|
|背单词；想要搞一个从上面的词汇表中自动出题的小程序考自己|写了个自动出题的程序|rust|
|军理要期末了，开卷考，准备打印ppt，但是ppt页数实在太多了，想着可能可以提取出文字|写了批量从ppt中提取文字的脚本|python|
|微信公众号文章想放到微信读书里听，但微信读书无法直接导入网页文章|写了个把微信公众号文章转成docx的脚本|python|

## 3. AI编程方法论

<!-- _class: trans navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* **方法论** *工具对比* *模型选择* *Copilot功能* *实战经验* -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 3.1 能力重点转移

<!-- _class: cols2_ul_sq fglass hugetext navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* **方法论** *工具对比* *模型选择* *Copilot功能* *实战经验* -->

- 理解即可，不需深入原理
- 增强环境配置能力
- 掌握常用技能基础
- 了解各语言特性差异
- 提高工程化能力
- 增强问题分解能力
- 提高需求转代码能力
- 系统集成与架构能力

## 3.2 编写高效提示词

<!-- _class: bq-purple hugetext navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* **方法论** *工具对比* *模型选择* *Copilot功能* *实战经验* -->

#### 提示词工程的核心原则

> 明确目标和要求
>
> 1.提供必要的上下文  (*即使是人你也得说明白要干啥他才能去做啊*)
> 2. 要简洁明了，避免冗余
> 3. 采用逐步指导的方式
> 4. 使用专业术语和明确的指令


## 3.3 环境配置能力

<!-- _class: cols-2-46 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* **方法论** *工具对比* *模型选择* *Copilot功能* *实战经验* -->

<div class="ldiv">

#### 使用包管理工具简化环境配置

右侧列举了三大系统常用的包管理器。特别留意Windows：
_Chocolatey极其好用，但知道的人不多_

#### 有些程序得在linux上跑 怎么办？

- VMWare Workstaton (不推荐。gui界面其实没太大意义)
- Windows Subsystem for Linux, WSL (强烈推荐！与Windows系统无缝衔接，Windows的资源管理器能看WSL2的文件，WSL2也能直接调用Windows的程序)

</div>

<div class="rdiv">

- **Windows**: Chocolatey
  ```powershell
  choco install nodejs python vscode git mingw
  ```

- **macOS**: Homebrew
  ```bash
  brew install node python visual-studio-code git
  ```

- **Linux**: apt/yum/...
  ```bash
  sudo apt install nodejs python3 git
  ```

</div>

## 4. AI编程工具对比与选择

<!-- _class: trans navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* **工具对比** *模型选择* *Copilot功能* *实战经验* -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 4.1 现有的AI编程工具

<!-- _class: cols-2-73 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* **工具对比** *模型选择* *Copilot功能* *实战经验* -->
<div class=ldiv>

#### 现有主流工具
- GitHub Copilot
- GitHub Copilot CLI
- Cursor
- WindSurf
- Aider
- Claude CLI
- OpenAI CLI
- ...

</div>

<div class=rdiv>

![h:350](https://github.githubassets.com/images/modules/site/copilot/productivity-bg-head.png)

</div>

## 4.2 工具对比分析

<!-- _class: caption navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* **工具对比** *模型选择* *Copilot功能* *实战经验* -->

| 工具 | 优势 | 劣势 | 适用场景 |
|------|------|------|----------|
| GitHub Copilot | IDE集成度高，实时建议 | 响应慢 | 日常编码，复杂项目 |
| Cursor | IDE集成度高，有强大的上下文理解 | 受微软限制 | 日常编码，复杂项目 |
| Aider | 命令行友好 | 总体能力偏差 | 日常编码 |
| Claude CLI | 强大的推理能力 | 集成度较低 | 日常编码 |

<div class="caption">
图1: AI编程工具对比表
</div>

## 4.3 为什么我认为GitHub Copilot > Cursor?

<!-- _class: cols-3 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* **工具对比** *模型选择* *Copilot功能* *实战经验* -->

<div class=ldiv>

#### 费用优势
- 学生可免费使用 (教育优惠)

</div>

<div class=mdiv>

#### 技术背景
- 微软与OpenAI合作
- 基于强大的GPT模型
- 持续快速迭代

</div>

<div class=rdiv>

#### 生态优势
- 与GitHub深度集成
- 跨平台IDE支持
- 丰富的附加功能

</div>

## 6. 如何选择AI模型

<!-- _class: navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* **模型选择** *Copilot功能* *实战经验*-->

不同任务适合不同的AI模型：

- **GPT-3.5**: 速度快，适合简单的代码补全
- **GPT-4**: 更强的理解能力，适合复杂问题
- **Claude**: 更好的文档生成和代码解释

参考资料：[*GitHub官方模型对比文档*](https://docs.github.com/en/copilot/using-github-copilot/ai-models/comparing-ai-models-using-different-tasks)

## 7. GitHub Copilot功能详解

<!-- _class: cols2_ul_ci fglass navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* **Copilot功能** *实战经验* -->

- **Inline Chat**: 编辑器内直接交流
- **Terminal Inline Chat**: 终端内AI辅助
- **自动生成Commit信息**: 提高提交质量
- **@workspace**: 工作区上下文访问
- **@vscode**: IDE功能集成
- **Copilot Chat**: 更强大的对话功能
- **Copilot Edit**: AI辅助编辑代码
- **Copilot Agent**: 自动化任务执行

## 8. 项目实战经验分享

<!-- _class: trans navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## 8.1 小项目实战指南

<!-- _class: fixedtitleA navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->

### 目标导向的提示词设计

```
为我创建一个Python脚本，它可以监控指定文件夹中的所有.md文件变化，
当文件发生变化时，自动使用pandoc将其转换为PDF格式。
需要支持命令行参数来指定监控的文件夹和输出路径。
```

比过程导向的提示词更有效：

```
我想写一个Python脚本，首先需要导入watchdog库，然后创建一个类...
```

## 8.2 小项目自动化案例

<!-- _class: cols-2-46 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->
<div class=ldiv>

### 自动化潜力
- 文件格式转换
- 数据处理脚本
- 日常任务自动化
- API调用封装
- 简单的GUI工具

</div>

<div class=rdiv>



</div>

## 8.3 大项目实战策略

<!-- _class: rows-2 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->

<div class="tdiv">

### 有效的项目管理方法

- 自定义项目整体架构
- 任务细分
- 快速定位和解决Bug
- 构建完善的测试集

</div>

<div class="bdiv">

![#center h:230](https://cdn.pixabay.com/photo/2018/05/08/08/44/artificial-intelligence-3382507_1280.jpg)

### AI辅助编程最适合的场景
- 重复性代码生成
- 样板代码快速实现
- 代码重构与优化
- 单元测试生成

</div>

## 8.4 Polaris项目展示

<!-- _class: fixedtitleB navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->

<div class="div">

#### Polaris: AI辅助开发的实际案例

Polaris是一个使用AI辅助开发的大型项目，展示了如何在复杂项目中有效运用AI编程工具:

1. 项目架构设计
2. 模块划分与API设计
3. 代码生成与重构
4. 测试覆盖

</div>

## 8.5 Git与AI集成实践

<!-- _class: cols-2 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->
<div class=ldiv>

### AI辅助Git工作流

- 自动生成有意义的commit信息
- 根据代码变更撰写PR描述
- 代码审查与问题识别
- 冲突解决建议

</div>

<div class=rdiv>

```bash
# 使用Copilot CLI生成commit信息
git add .
gh copilot suggest -t "commit"

# 使用Copilot生成PR描述
gh copilot suggest -t "pr-description"

# 代码审查
gh copilot explain "path/to/file.js"
```

</div>

## 8.6 大项目开发一般方法

<!-- _class: bq-green navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->

> ### AI辅助大型项目开发流程
> 
> 1. **确定项目架构**：先自行设计整体框架
> 
> 2. **任务分解**：将复杂任务拆分为小模块
> 
> 3. **增量开发**：逐步实现功能并集成
> 
> 4. **测试驱动**：先写测试，再用AI生成实现
> 
> 5. **持续优化**：利用AI提出的改进建议

## 9. 拓展内容：MCP服务器

<!-- _class: cols-2-64 navbar -->
<!-- _header: \ ***@AI辅助编程*** *环境配置* *重要意义* *方法论* *工具对比* *模型选择* *Copilot功能* **实战经验** -->
<div class=ldiv>

### MCP服务器项目

- 使用方法
  - 安装配置
  - 常用命令
  - 最佳实践

- 开发过程
  - AI辅助编程示例
  - 自动化测试

- 逆向工程应用
  - IDA Pro集成
  - 逆向分析

</div>

<div class=rdiv>

```python
# MCP Server示例代码
class MCPServer:
    def __init__(self, host='0.0.0.0', port=8080):
        self.host = host
        self.port = port
        self.routes = {}
    
    def register_route(self, path, handler):
        self.routes[path] = handler
    
    def start(self):
        # 启动服务器代码
        print(f"MCP Server running on {self.host}:{self.port}")
        # ...

# 使用AI生成的路由处理器
def generate_route_handler(route_spec):
    # 使用AI根据规格生成路由处理器
    # ...
    return handler
```

GitHub仓库: [github.com/user/mcp-server](https://github.com/user/mcp-server)

</div>

---

<!-- _class: lastpage -->
<!-- _footer: "" -->

###### 谢谢观看！ 

<div class="icons">
- <i class="fa-solid fa-envelope"></i>
  - 邮箱：23300240006@m.fudan.edu.cn
- <i class="fa-brands fa-weixin"></i> 
  - 微信：p18616702662
- <i class="fa-solid fa-house"></i> 
  - GitHub: dywsy21
<div>
