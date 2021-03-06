---

copyright:
years: 2016

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 其他测试
{: #etn_next}
上次更新时间：2016 年 10 月 7 日
{: .last-updated}

以下测试是在“高安全性业务网络”环境（除非另有说明）中运行的，用于测试链代码功能、分类帐、长时间运行、并行性和复杂交易。验证程序和成员资格服务节点均以 VM 访客身份在 LinuxONE 操作系统上的安全服务容器内运行。下面使用的值是根据客户输入而选择的，不要将其误解为最大值。（注：其中某些测试会在 [Node.js SDK](etn_txn.html) 以及[测试共识和可用性](etn_pbft.html)部分中重复。）

{:shortdesc}

1. 链代码功能 - 执行了链代码接口，以确保 `Deploy`、`Invoke` 和 `Query` 交易能够使用 REST API 和 CLI 正常运行。REST API 和 CLI 都用于测试所有端点功能，包括区块、区域链、链代码、网络、注册器和交易，如“Hyperledger 协议规范”中所述。
2. 分类帐 - 根据不同的驱动环境，在分类帐中创建 1K 有效内容，包含 20,000 条记录。测试包含一台客户机，用于以序列化方式创建 20,000 条记录。
3. 长时间运行 - 此测试的执行方式是使用 example02 演示链代码在 72 小时内跨多个节点发送调用、链高度和查询。
4. Node.js SDK - 增强的 Node.js SDK 用于以开发方式（通过 `peer node start –peer` 启动同级）和网络方式（通过 `peer node start –peer -chaincodedev` 启动同级）在同级上注册和登记用户以及执行部署、调用和查询。
5. 基本并行性 - 此测试的执行方式是在 10 分钟持续时间内，使用 1KB 有效内容向四个同级分别发送并行调用，然后度量链高度并查询分类帐状态。
6. 复杂交易 - 此测试的执行方式是在 10 分钟持续时间内，随机将各种有效内容大小（范围从 10K 到 500K）的查询和调用的组合提交给同级。接着会度量链高度并查询全局状态，以确保共享分类帐跨网络同级保持同步。
