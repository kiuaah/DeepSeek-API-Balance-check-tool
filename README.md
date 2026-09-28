# DeepSeek API Balance Check Tool

一个极简、轻量的 **原生 Android DeepSeek API 余额查询工具**，用于随时查看 DeepSeek 账户的 CNY 余额、今日用量和当前峰谷时段，并支持桌面小组件。

> 非 DeepSeek 官方项目，仅供个人查询与管理使用。

## 核心功能

- 查询 DeepSeek API 的 **CNY 总余额**
- 进入应用后自动查询一次
- 点击“查询余额”立即刷新
- 今日用量根据每日余额变化自动累计
- 每日 0 点自动查询并重置今日用量基线
- 显示当前为“高峰时段”或“空闲时段”
- 显示 UTC+8 当前时间
- 显示距离下次时段切换的秒级倒计时
- 高峰状态使用深红色文字，空闲状态使用灰色文字

## 效果展示

<img width="122" height="265" alt="Screenshot_2026-09-28-16-34-15-918_com deepseek b" src="https://github.com/user-attachments/assets/90d49c9f-cf62-4b43-8391-c2f104b43a32" />
<img width="122" height="265" alt="Screenshot_2026-09-28-14-56-35-214_com miui home" src="https://github.com/user-attachments/assets/0e695796-9dd8-48ab-9297-f1387c9289ca" />


## 刷新频率

点击应用中的刷新频率文字，可设置前台刷新间隔：

```text
1 秒、5 秒、10 秒、15 秒、30 秒
1 分钟、5 分钟、10 分钟、15 分钟
```

长按同一位置，可设置小组件后台查询频率：

```text
1 秒、5 秒、10 秒、30 秒
1 分钟、5 分钟、10 分钟、30 分钟、1 小时
```

后台刷新会受 Android、澎湃 OS 的省电策略和系统调度限制。

## 峰谷时段

根据规则自动判断：

- 周一至周五 `09:00-12:00`、`14:00-18:00`：高峰时段
- 其余时间：空闲时段
- 周末全天：空闲时段
- 中国法定节假日全天：空闲时段
- 空闲时段价格按高峰价格的 50% 计算

节假日数据会从公开年度数据源自动更新，并缓存到本机；网络不可用时回退到内置数据。

## 桌面小组件

提供三种尺寸：

- `2×1`：余额和今日用量，紧凑窄卡片
- `2×2`：固定正方形，余额、今日用量、当前时段
- `4×2`：余额、今日用量、当前时段

小组件特点：

- 黑灰极简设计
- 无查询按钮
- 点击整个小组件即可打开应用并刷新
- 小组件中不显示秒级倒计时

## 隐私设计

- 不内置 API Key
- API Key 只发送给 `api.deepseek.com`
- 勾选“记住密钥”后，仅保存在应用私有存储中
- 不接入第三方统计、广告或云服务
- 无第三方依赖库

## 技术实现

- 原生 Java Android 应用
- `HttpURLConnection` 请求官方接口
- `RemoteViews` 实现桌面小组件
- `AlarmManager` 调度后台查询和每日 0 点任务
- 无 Gradle 构建
- 使用 Android SDK 命令行工具编译
- 支持 Android 6.0 及以上
- 目标 Android 15
- APK 体积约 42 KB

## 项目地址

```text
https://github.com/kiuaah/DeepSeek-API-Balance-check-tool
```

## 适用场景

适合个人开发者、DeepSeek API 用户、需要随时查看余额和峰谷时段的用户，以及希望使用超轻量桌面小组件的 Android 用户。
