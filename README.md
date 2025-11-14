# 星汉·拟真流体 - 中国风天气海报

<div align="center">

![Gemini 3.0 Pro](https://img.shields.io/badge/Generated%20by-Gemini%203.0%20Pro-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=for-the-badge&logo=three.js&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=for-the-badge&logo=webgl&logoColor=white)
![GLSL](https://img.shields.io/badge/GLSL-5586A4?style=for-the-badge)

一个基于 **Three.js** 和 **GLSL** 的新中式风格交互式天气海报，具有电影级高拟真物理特效。

**✨ 本项目完全由 Google Gemini 3.0 Pro 生成 ✨**

[在线演示](#) | [技术文档](./完美复刻提示词.md)

</div>

---

## 🤖 AI 生成说明

> **本项目是 AI 原生应用的典范案例**

本项目的**所有代码**（包括 1000+ 行 GLSL 着色器、Three.js 场景管理、UI/UX 设计）均由 **Google Gemini 3.0 Pro** 一次性生成，无需人工修改即可完美运行。

### 生成亮点

- ✅ **完整的双引擎渲染架构**：AI 自主设计了分离式粒子系统
- ✅ **复杂的物理模拟算法**：星空闪烁、雪花飘荡、雨水倾斜等真实物理效果
- ✅ **1200+ 行单文件代码**：结构清晰，注释完善，开箱即用
- ✅ **新中式美学设计**：磨砂玻璃 UI + 传统诗词排版 + 书法字体
- ✅ **丰富的内容系统**：12首诗词 + 5个城市 = 60种场景组合
- ✅ **完美的响应式适配**：桌面端和移动端自动切换布局
- ✅ **高性能优化**：粒子数量控制、混合模式优化、平滑插值
- ✅ **数据驱动架构**：易于扩展和维护的状态管理系统

> 💡 **这证明了 Gemini 3.0 Pro 在复杂 WebGL 应用开发中的卓越能力**

---

## ✨ 项目简介

**星汉·拟真流体**是一个融合了传统中国美学与现代 WebGL 技术的单页网页应用。项目通过 AI 精心设计的粒子系统和自定义着色器，实现了四种极具真实感的天气场景，每种场景都配有相应的中国古典诗词，营造出独特的意境美。

### 🎯 核心特点

- **双引擎渲染架构**：分离式粒子系统设计，优化不同天气效果的渲染性能
- **电影级物理模拟**：基于 GLSL 的真实物理计算，模拟星空、雨夜、飞雪、狂风四种天气
- **新中式美学设计**：磨砂玻璃质感 UI + 传统书法字体 + 古典诗词排版
- **丰富的诗词库**：12首精选古典诗词，每种天气3首可切换
- **多城市支持**：5个中国古都（长安、洛阳、金陵、姑苏、临安）自由切换
- **高性能优化**：克制的粒子数量（6000-8000颗），保证流畅运行
- **完美响应式**：桌面端竖排诗词，移动端自动横排，无缝适配

---

## 🛠️ 技术栈

```
🤖 AI 引擎      - Google Gemini 3.0 Pro（代码生成）
HTML5          - 单文件结构
Tailwind CSS   - 原子化 CSS 框架
Three.js       - WebGL 3D 场景渲染
GLSL           - 自定义着色器（粒子物理模拟）
Lucide Icons   - 现代图标库
Google Fonts   - Noto Serif SC（衬线体）+ Zhi Mang Xing（书法体）
```

> **特别说明**：本项目使用 Gemini 3.0 Pro 根据[详细提示词](./完美复刻提示词.md)一次性生成，展示了大语言模型在复杂前端工程中的实战能力。

---

## 🏗️ 核心架构

### 双引擎渲染系统

#### 引擎一：通用粒子系统 (Particle Engine)
- **技术**：`THREE.Points` + `ShaderMaterial`
- **用途**：渲染点状粒子（晴空、飞雪、狂风）
- **粒子数**：6000-8000 颗
- **Shader 属性**：
  - `size` - 粒子大小
  - `speed` - 速度因子
  - `randomVal` - 随机种子

#### 引擎二：雨水系统 (Rain Engine)
- **技术**：`THREE.InstancedMesh` + `ShaderMaterial`
- **用途**：专门渲染雨天效果
- **几何体**：`THREE.PlaneGeometry`（细长平面）
- **粒子数**：1000-2000 条雨丝
- **Shader 属性**：
  - `instancePos` - 实例位置
  - `instanceSpeed` - 实例速度
  - `instanceHeight` - 雨丝长度

---

## 🌤️ 四种天气模式

### 模式 0：晴空 (Stars) 🌙

**物理特性**：
- ✨ 位置固定，星星不移动
- 💫 脉冲闪烁：使用 `sin(uTime * 2.0 + randomVal * 10.0)` 模拟大气扰动
- ☄️ 流星系统：独立流星线，5% 概率随机生成
- 👆 交互：极微弱的视差效果 (Parallax)

**诗词**：醉后不知天在水，满船清梦压星河

---

### 模式 1：雨夜 (Rain) 🌧️

**物理特性**：
- ⚡ 高速下落：`mod(uTime * speed, 1200.0)` 实现循环下落
- 🌬️ 倾斜雨丝：`xDrift = -yDrop * 0.2` 模拟风吹效果
- ☂️ 交互："避雨"效果，鼠标附近雨丝被推开
- 🎨 视觉：半透明蓝白色，模拟高速运动残影

**诗词**：君问归期未有期，巴山夜雨涨秋池

---

### 模式 2：飞雪 (Snow) ❄️

**物理特性**：
- 🌊 空气动力学：叠加正弦波 (`swayX + flutter`) 模拟飘荡和翻滚
- 📏 速度差异：大雪花快，小雪花慢（由 `speed` 属性调节）
- 💨 交互：强烈的鼠标排斥效果，仿佛风吹开雪花
- ⚪ 视觉：柔和雾状边缘，线性透明度衰减

**诗词**：柴门闻犬吠，风雪夜归人

---

### 模式 3：狂风 (Wind) 💨

**物理特性**：
- 🌪️ 风洞湍流：高速水平移动 `xOffset = mod(uTime * windSpeed, 2000.0)`
- 📳 剧烈抖动：Y 轴叠加高频 sin 抖动，模拟沙尘卷起
- 🌀 交互：鼠标产生"漩涡" (Vortex) 效果
- 👻 视觉：半透明烟尘质感，忽明忽暗

**诗词**：大风起兮云飞扬，威加海内兮归故乡

---

## 🎭 交互功能

### 📜 诗词切换系统

**功能特点：**
- 🔄 每种天气配备 **3首** 经典古诗词
- ⬅️➡️ 点击诗词两侧箭头按钮切换
- 💫 平滑的淡入淡出动画（300ms）
- 🔘 底部圆点指示器显示当前位置
- 🎯 切换天气时自动重置到第一首

**诗词库（共12首）：**

| 天气 | 诗词 1 | 诗词 2 | 诗词 3 |
|------|--------|--------|--------|
| 🌙 晴空 | 醉后不知天在水<br>满船清梦压星河 | 天阶夜色凉如水<br>坐看牵牛织女星 | 迢迢牵牛星<br>皎皎河汉女 |
| 🌧️ 雨夜 | 君问归期未有期<br>巴山夜雨涨秋池 | 夜阑卧听风吹雨<br>铁马冰河入梦来 | 春雨断桥人不度<br>小舟撑出柳阴来 |
| ❄️ 飞雪 | 柴门闻犬吠<br>风雪夜归人 | 千里黄云白日曛<br>北风吹雁雪纷纷 | 窗含西岭千秋雪<br>门泊东吴万里船 |
| 💨 狂风 | 大风起兮云飞扬<br>威加海内兮归故乡 | 长风破浪会有时<br>直挂云帆济沧海 | 八月秋高风怒号<br>卷我屋上三重茅 |

---

### 🗺️ 地点切换系统

**功能特点：**
- 🏛️ 收录 **5个** 中国古都
- 🖱️ 点击左上角城市名称即可切换
- 🔄 悬浮时显示刷新图标提示
- 📅 每个城市配有独特的农历节日
- 🌡️ 温度根据城市和天气自动联动

**城市数据：**

| 城市 | 英文 | 农历节日 | 基准温度 | 特色 |
|------|------|----------|----------|------|
| 🏛️ 长安 | CHANG'AN | 上元 · 夜 | 18°C | 盛唐古都 |
| 🌸 洛阳 | LUOYANG | 中秋 · 宵 | 16°C | 牡丹花城 |
| 🌊 金陵 | JINLING | 寒食 · 暮 | 14°C | 六朝古都 |
| 🏞️ 姑苏 | GUSU | 清明 · 春 | 19°C | 江南水乡 |
| 🏔️ 临安 | LIN'AN | 重阳 · 秋 | 17°C | 南宋都城 |

**温度计算逻辑：**
```
晴空：基准温度
雨夜：基准温度 - 3°C
飞雪：基准温度 - 23°C
狂风：基准温度 - 9°C
```

**内容组合：**
- 总诗词数：12首
- 总城市数：5个
- 总组合数：**12 × 5 = 60种** 不同场景

---

## 🎨 UI/UX 设计

### 新中式美学

- **磨砂玻璃质感**：`backdrop-filter: blur(20px)` + `rgba(0,0,0,0.3)`
- **字体组合**：
  - Noto Serif SC - 主标题和温度（衬线体）
  - Zhi Mang Xing - 诗词（书法体）
- **布局结构**：
  ```
  左上角 - 地点（长安）
  左下角 - 温度 + 天气图标
  中右侧 - 古典诗词（桌面竖排，移动端横排）
  底部   - 圆角胶囊 Dock 栏（4 个天气切换按钮）
  ```

### 交互动画

- **平滑过渡**：天气切换时使用 `requestAnimationFrame` 进行 800ms 插值动画
- **UI 动画**：文字"淡出 → 更新内容 → 淡入"，配合模糊效果
- **按钮反馈**：激活状态带有缩放和光点指示器
- **诗词遮罩**：径向渐变遮罩，制造若隐若现的意境

---

## 🚀 快速开始

> **提示**：本项目是由 Gemini 3.0 Pro 生成的单文件应用，无需任何构建工具或依赖安装！

### 安装

```bash
# 克隆仓库
git clone https://github.com/Jasonliu-0/xinghan-weather-poster.git

# 进入目录
cd xinghan-weather-poster
```

### 运行

直接在浏览器中打开 `index.html` 文件即可，或使用本地服务器：

```bash
# 使用 Python 3
python -m http.server 8000

# 使用 Node.js (需要安装 http-server)
npx http-server -p 8000

# 使用 VSCode Live Server 扩展
右键 index.html → Open with Live Server
```

访问 `http://localhost:8000` 即可查看效果。

### 使用说明

**切换天气：**
- 点击底部 Dock 栏的4个图标按钮
- 🌙 晴空 | 🌧️ 雨夜 | ❄️ 飞雪 | 💨 狂风

**切换诗词：**
- 点击诗词两侧的 `⬅️` `➡️` 箭头按钮
- 观察底部圆点指示器了解当前位置
- 每种天气有3首不同的古诗词

**切换城市：**
- 点击左上角的城市名称（如"长安"）
- 循环切换5个古都：长安 → 洛阳 → 金陵 → 姑苏 → 临安
- 温度会根据城市和天气自动变化

---

## 📁 项目结构

```
xinghan-weather-poster/
├── index.html              # 主文件（包含所有代码，由 Gemini 3.0 Pro 生成）
├── 完美复刻提示词.md        # 提示词工程文档（输入给 AI 的完整需求）
└── README.md               # 项目文档
```

---

## 🔄 如何使用 Gemini 3.0 Pro 复现此项目

想要复现或改进本项目？按照以下步骤操作：

### 步骤 1：准备提示词

查看 [`完美复刻提示词.md`](./完美复刻提示词.md) 文件，这是输入给 Gemini 3.0 Pro 的完整技术规格。

**提示词特点**：
- 📋 明确的技术栈要求（HTML + Tailwind + Three.js + GLSL）
- 🏗️ 详细的架构设计（双引擎渲染系统）
- 🎨 具体的物理模拟规则（四种天气模式）
- 💡 清晰的 UI/UX 要求（新中式美学）

### 步骤 2：调用 Gemini 3.0 Pro

在 [Google AI Studio](https://aistudio.google.com/) 或通过 API 调用：

```python
# 示例代码（使用 Python SDK）
import google.generativeai as genai

genai.configure(api_key='YOUR_API_KEY')
model = genai.GenerativeModel('gemini-3.0-pro')

# 读取提示词
with open('完美复刻提示词.md', 'r', encoding='utf-8') as f:
    prompt = f.read()

# 生成代码
response = model.generate_content(prompt)
print(response.text)
```

### 步骤 3：保存并运行

将 Gemini 生成的代码保存为 `index.html`，直接在浏览器中打开即可运行！

### 修改与扩展

想要添加新功能？在提示词中添加需求即可：

```markdown
模式 4：流云 (Clouds) ☁️
- 使用体积云算法（Volumetric Clouds）
- 鼠标交互：云朵会随鼠标"散开"
- 诗词：行到水穷处，坐看云起时
```

然后重新调用 Gemini 3.0 Pro 生成新版本！

---

## 🔧 技术实现亮点

### 1. GLSL 着色器优化

```glsl
// 星星闪烁算法 - 模拟大气扰动
float twinkle = sin(uTime * 2.0 + randomVal * 10.0);
twinkle = smoothstep(-0.2, 1.0, twinkle);
vAlpha = 0.3 + 0.7 * twinkle;
```

### 2. 雪花飘荡物理模拟

```glsl
// 叠加正弦波模拟复杂空气流动
float swayX = sin(uTime * 0.5 + pos.y * 0.005 + randomVal * 10.0) * 20.0;
float flutter = sin(uTime * 3.0 + randomVal * 100.0) * 2.0;
pos.x += swayX + flutter;
```

### 3. 雨丝倾斜与避雨效果

```glsl
// 倾斜计算
float xDrift = -yDrop * 0.2;

// 避雨逻辑
if (d < 180.0) {
    float force = (180.0 - d) / 180.0;
    pos.x += (pos.x - uMouse.x) * force * 0.8;
}
```

### 4. 流星生成系统

```javascript
// 5% 概率生成流星（仅晴天）
if (Math.random() > 0.05) return;
meteor.userData = { 
    vel: new THREE.Vector3(-15 - Math.random()*10, -10 - Math.random()*10, 0), 
    life: 1.0 
};
```

### 5. 诗词切换系统

```javascript
// 数据驱动的诗词库
const weatherPoems = [
    // 晴空
    [
        { p1: '醉后不知天在水', p2: '满船清梦压星河', m: '星河欲转', s: 'Starry Night' },
        { p1: '天阶夜色凉如水', p2: '坐看牵牛织女星', m: '银汉迢迢', s: 'Milky Way' },
        { p1: '迢迢牵牛星', p2: '皎皎河汉女', m: '河汉清浅', s: 'Stars Above' }
    ],
    // ... 其他天气模式
];

// 循环切换算法
function changePoemIndex(direction) {
    const poems = weatherPoems[currentWeatherMode];
    currentPoemIndex = (currentPoemIndex + direction + poems.length) % poems.length;
    updatePoemUI();
}
```

### 6. 地点联动系统

```javascript
// 城市数据结构
const locations = [
    { zh: '长安', en: 'CHANG\'AN', lunar: '上元 · 夜', temp: 18 },
    { zh: '洛阳', en: 'LUOYANG', lunar: '中秋 · 宵', temp: 16 },
    // ...
];

// 温度联动计算
const temps = [
    location.temp,        // 晴空
    location.temp - 3,    // 雨夜
    location.temp - 23,   // 飞雪
    location.temp - 9     // 狂风
];
```

### 7. 动态指示器生成

```javascript
// 根据诗词数量动态生成指示器
function updatePoemIndicator() {
    const poems = weatherPoems[currentWeatherMode];
    indicator.innerHTML = poems.map((_, i) => 
        `<span class="w-2 h-2 rounded-full transition-all duration-300 
         ${i === currentPoemIndex ? 'bg-white/70 w-6' : 'bg-white/20'}">
         </span>`
    ).join('');
}
```

---

## 📱 响应式设计

| 屏幕尺寸 | 字体调整 | 诗词排版 | 布局变化 |
|---------|---------|---------|---------|
| 桌面端 (>768px) | 大号字体 | 竖排 (`vertical-rl`) | 诗词右侧居中 |
| 移动端 (≤768px) | 小号字体 | 横排 (`horizontal-tb`) | 诗词屏幕正中 |

```css
@media (max-width: 768px) { 
    .vertical-text { 
        writing-mode: horizontal-tb; 
        letter-spacing: 0.2em; 
    } 
}
```

---

## ⚡ 性能优化

- **粒子数量控制**：6000-8000 颗（通用系统），1000-2000 条（雨水系统）
- **PixelRatio 限制**：`Math.min(window.devicePixelRatio, 2)` 避免超高分辨率性能问题
- **深度写入禁用**：`depthWrite: false` 提升透明粒子渲染性能
- **加法混合模式**：`THREE.AdditiveBlending` 实现自然发光效果
- **平滑插值优化**：鼠标位置使用 `lerp(0.1)` 平滑过渡，避免抖动

---

## 🎯 浏览器兼容性

| 浏览器 | 最低版本 | 备注 |
|--------|---------|------|
| Chrome | 90+ | ✅ 推荐 |
| Firefox | 88+ | ✅ 完美支持 |
| Safari | 14+ | ✅ 支持 |
| Edge | 90+ | ✅ 推荐 |
| Opera | 76+ | ✅ 支持 |

**系统要求**：支持 WebGL 2.0 的显卡和浏览器

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 📄 开源协议

本项目采用 [MIT](LICENSE) 协议开源。

---

## 🙏 致谢

### AI 技术支持

- **Google Gemini 3.0 Pro** - 本项目的核心开发者，展示了 AI 在复杂 WebGL 应用开发中的强大能力

### 开源库与资源

- **Three.js** - 强大的 WebGL 库
- **Tailwind CSS** - 高效的原子化 CSS 框架
- **Lucide Icons** - 优雅的开源图标集
- **Google Fonts** - 提供中文字体支持

### 关于 AI 辅助开发

本项目证明了现代大语言模型（LLM）已经具备以下能力：

1. **完整架构设计**：从零设计双引擎渲染系统
2. **复杂算法实现**：编写高性能 GLSL 着色器和物理模拟算法
3. **美学与技术融合**：在代码中体现新中式美学理念
4. **工程化实践**：性能优化、响应式设计、兼容性处理

**开发流程**：
```
提示词工程 → Gemini 3.0 Pro 生成 → 零修改部署 ✅
```

> 这标志着 AI 原生应用开发的新纪元

---

## 📞 联系方式

如有问题或建议，欢迎通过以下方式联系：

- Issue：[GitHub Issues](https://github.com/Jasonliu-0/xinghan-weather-poster/issues)
- Email：your.email@example.com

---

<div align="center">

**星汉·拟真流体** © 2025

🤖 **Powered by Google Gemini 3.0 Pro** 🤖

用代码书写诗意，用科技传承文化

*本项目是 AI 原生应用的探索与实践*

---

[![Gemini](https://img.shields.io/badge/Generated%20by-Gemini%203.0%20Pro-4285F4?style=flat-square&logo=google)](https://ai.google.dev/)
[![Three.js](https://img.shields.io/badge/Three.js-r128-000000?style=flat-square&logo=three.js)](https://threejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

</div>

