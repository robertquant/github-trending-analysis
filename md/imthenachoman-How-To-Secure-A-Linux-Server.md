# How-To-Secure-A-Linux-Server - Linux 服务器安全加固全方位实战指南

> **An evolving how-to guide for securing a Linux server**

| 指标 | 数据 |
|------|------|
| GitHub | [imthenachoman/How-To-Secure-A-Linux-Server](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server) |
| Stars | 26,834 |
| 今日新增 | +233 |
| 语言 | Shell / Markdown |
| 许可证 | CC-BY-SA-4.0 |
| Forks | 1,700+ |
| 提交数 | 269 |

---

## 项目简介与核心功能

**How-To-Secure-A-Linux-Server** 是由 Anchal Nigam (imthenachoman) 创建并维护的开源指南项目，旨在提供一个**全面、循序渐进、可直接实操**的 Linux 服务器安全加固教程。

> 这是一份"一站式"指南——作者找不到任何一个涵盖所有内容的教程，于是自己写了一个。

### 核心亮点

- **SSH 安全加固** — Ed25519 密钥认证、禁用密码登录、2FA/MFA 双因素、AllowGroups 限制
- **防火墙与入侵检测** — UFW 默认拒绝策略、PSAD 网络层检测、Fail2Ban + CrowdSec 应用层防护
- **系统审计** — AIDE 文件完整性监控、ClamAV 杀毒、Rkhunter/chkrootkit Rootkit 检测、Lynis 安全审计
- **基础加固** — sudo/su 权限控制、密码策略、自动安全更新、/proc 隐藏进程、FireJail 沙箱
- **高级/危险区** — 内核 sysctl 硬化、GRUB 密码保护、禁用 Root 登录、umask 调整
- **Ansible 自动化** — 社区配套项目提供完整的 Playbook

---

## 技术架构与特点

### 架构层次

| 层次 | 技术方案 |
|------|----------|
| SSH 层 | 密钥认证 + 2FA + 端口变更 + 连接限制 |
| 网络层 | UFW 出入站规则 + PSAD iptables 日志分析 |
| 应用层 | Fail2Ban / CrowdSec 日志监控与自动封禁 |
| 审计层 | AIDE 文件完整性 + ClamAV 杀毒 + Rootkit 检测 |
| 内核层 | sysctl 参数调优 + GRUB 保护 |

### 设计特点

- **发行版无关** — 以 Debian 为例但适用所有 Linux
- **可复制粘贴** — 几乎每步都提供可执行的命令片段
- **安全第一** — 先备份再修改，自动验证变更
- **邮件告警** — 集成 Exim4 + Gmail 发送安全通知
- **"懒惰"友好** — 提供 `sed`/`echo` 一行命令自动化配置

---

## 应用场景

### 家庭 / 个人服务器
- 自建 NAS、HomeAssistant 等智能家居服务器
- 个人博客、VPN、文件共享服务器
- 家庭实验室 (Home Lab) 环境

### 小型团队 / 创业公司
- 初创公司的基础设施安全基线
- 远程办公 VPN 服务器加固
- 开发/测试服务器安全初始化

### 学习 / 教育
- Linux 安全入门教学的优秀教材
- 网络安全课程实操参考
- DevOps / SRE 安全意识培训

---

## 为什么火 (Trending 原因)

1. **安全事件频发** — 近年大规模数据泄露事件不断，个人和小团队安全意识空前觉醒
2. **"一站式"稀缺性** — 市面上安全教程碎片化严重，这份指南是少见的完整方案
3. **实战导向** — 不是枯燥的安全理论，而是可以直接复制粘贴执行的命令
4. **持续演进** — 269 次提交，社区持续贡献新内容，保持与时俱进
5. **CC-BY-SA 开源许可** — 自由分享和修改，降低了安全知识的获取门槛
6. **Ansible 生态** — 配套自动化项目让安全加固从"手工活"变成"一键部署"

---

## 同类项目对比

| 项目 | 覆盖范围 | 实操性 | 自动化 | 社区规模 |
|------|----------|--------|--------|----------|
| **本指南** | 全方位 (SSH/网络/审计/内核) | 极高 (可复制粘贴) | 有 Ansible 配套 | 26.8K Stars |
| CIS Benchmarks | 全方位 (行业标准) | 中等 (需自行解读) | 部分 | 企业级 |
| Arch Wiki Security | 中等 (Arch 偏向) | 中等 | 无 | 社区 Wiki |
| pratiktri/server_init_harden | 基础 | 高 (Bash 脚本) | 自带脚本 | 较小 |
| os-hardening (Ansible) | 中等 | 高 (Ansible) | 原生 Ansible | 中等 |

---

## 适合谁使用

### 强烈推荐
- **自建服务器的个人用户** — 家里有 NAS、家庭服务器的人
- **Linux 初学者** — 想了解服务器安全的入门者
- **小型创业团队** — 没有专职安全人员的团队
- **DevOps / SRE 工程师** — 作为安全基线参考
- **网络安全学生** — 系统学习 Linux 安全加固

### 注意事项
- 企业级场景需结合 CIS Benchmark 和专业安全团队
- 容器化环境需另寻安全方案
- 非 Debian 系统部分命令需适配
- "危险区"操作（内核硬化、禁用 Root 等）需谨慎评估

---

## 快速上手指南

### 1. 阅读全文，了解全貌

在开始之前，完整阅读一遍指南，根据你的威胁模型（Threat Model）决定需要执行哪些步骤。

### 2. SSH 安全加固

```bash
ssh-keygen -t ed25519
sudo groupadd sshusers
sudo usermod -a -G sshusers your_username
```

### 3. 安装防火墙

```bash
sudo apt install ufw
sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw limit in ssh
sudo ufw enable
```

### 4. 部署入侵检测

```bash
# Fail2Ban 方式
sudo apt install fail2ban

# 或使用 CrowdSec（推荐）
curl -s https://install.crowdsec.net | sudo sh
sudo apt install crowdsec crowdsec-firewall-bouncer-iptables
```

### 5. 自动化方式（可选）

```bash
git clone https://github.com/moltenbit/How-To-Secure-A-Linux-Server-With-Ansible
# 编辑 variables.yml 后运行
ansible-playbook --inventory hosts.yml --ask-pass main-playbook.yml
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 7.0/10 | 非技术创新，但"一站式整合"思路在安全领域极具价值 |
| 代码质量 | 8.8/10 | 命令示例经过社区验证，注释清晰，带备份机制 |
| 实用性 | 9.8/10 | 直接可用的实战指南，几乎零学习成本 |
| 文档完善度 | 9.5/10 | 每个步骤都有 Why/How/References，内容极其详尽 |
| 社区活跃度 | 9.0/10 | 26.8K Stars，269 次提交，持续接受社区贡献 |

### **综合评分：8.6 / 10**

---

*分析日期：2026-05-14 | 数据来源：GitHub Trending + Web Research*

*GitHub: [imthenachoman/How-To-Secure-A-Linux-Server](https://github.com/imthenachoman/How-To-Secure-A-Linux-Server)*
