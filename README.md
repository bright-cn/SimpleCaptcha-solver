# SimpleCaptcha 求解器

[![宣传图](https://github.com/luminati-io/LinkedIn-Scraper/raw/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)

使用 Bright Data 先进的 CAPTCHA 求解技术轻松绕过 SimpleCaptcha。借助机器学习算法、[自动 IP 轮换](https://www.bright.cn/solutions/rotating-proxies)以及强大的代理基础设施，确保持续并稳定地访问目标站点。

Bright Data 的 CAPTCHA 求解器内置于我们的 [**抓取浏览器**](https://www.bright.cn/products/scraping-browser) 和 [**网络解锁器 API**](https://www.bright.cn/products/web-unlocker) 中，为处理最复杂的 CAPTCHA 挑战提供全面的解决方案。

## 功能特性  
- **快速求解 CAPTCHA**：自动且高效地识别并求解 SimpleCaptcha。  
- **IP 轮换**：通过自动重试和动态 IP 调整避免封禁。  
- **浏览器指纹模拟**：模拟真实用户活动，[绕过高级反爬机制](https://www.bright.cn/blog/web-data/anti-scraping-techniques)。  
- **JavaScript 渲染**：轻松处理 JavaScript 密集型网站的动态内容。  
- **全球地域覆盖**：精准解锁任何区域的内容。  
- **无缝集成**：可与 Puppeteer、Playwright 及 Selenium 等工具轻松配合使用。  
- **事件监控**：追踪 CAPTCHA 求解事件，例如检测、成功或失败。  

## 为什么选择 SimpleCaptcha 求解器

### **全球 20,000+ 客户的信赖**  
Bright Data 的 CAPTCHA 求解器因其可靠性及高性能，广受开发者、企业及各类机构的信任。

### **由高级代理网络驱动**  
基于超 1 亿 IP 及高级地理定位技术，我们的代理基础设施可确保流畅、不间断的 CAPTCHA 求解过程。

### **AI 驱动的 CAPTCHA 求解**  
我们的 CAPTCHA 求解器使用先进的 AI 逻辑来自动检测、分析并求解 CAPTCHA。它可处理重试、指纹模拟和请求头等，以绕过最复杂的反爬措施。

### **为开发者而生**  
- 轻松集成到 Puppeteer、Playwright 和 Selenium。  
- 可高度自定义 CAPTCHA 求解策略。  
- 自动重试和动态 IP 调整，保证抓取不中断。

> **专业提示 💡**  
>> 已经有自己的 CAPTCHA 求解方案？ 使用我们的 [Puppeteer 代理](https://www.bright.cn/integration/puppeteer)、[Playwright 代理](https://www.bright.cn/integration/playwright)以及 [Selenium 代理](https://www.bright.cn/integration/selenium) 进一步降低遇到 CAPTCHA 的风险。

## 工作原理

Bright Data 的 CAPTCHA 求解器集成于 **抓取浏览器** 和 **网络解锁器**，让求解 CAPTCHA 更加轻松。

### **自动求解 CAPTCHA**  
CAPTCHA 求解器会自动实时检测并识别 CAPTCHA。只需启用该功能，求解器就能从发现到完成全程处理。

### **为 SimpleCaptcha 定制化选项**  
```javascript
// 为不同的 CAPTCHA 类型定义默认选项
function getCaptchaOptions(captchaType, customOptions = {}) {
  const defaultOptions = {
    timeout: 30000, // 等待求解 CAPTCHA 的最长时间（毫秒）
    check_timeout: 500, // 检查 CAPTCHA 状态的间隔（毫秒）
    wait_networkidle: { timeout: 1000 }, // 网络空闲等待 1 秒
    debug: false // 调试模式（默认关闭）
  };

  // 为特定 CAPTCHA 类型定义选择器
  const captchaSelectors = {
    DataDome: { selector: '#datadome-captcha', success_selector: '#captcha-success' },
    reCAPTCHA: { selector: '.g-recaptcha', success_selector: '.recaptcha-success' },
    ClickCaptcha: { selector: '.click-captcha', success_selector: '.captcha-passed' },
    hCaptcha: { selector: '.h-captcha', success_selector: '.hcaptcha-success' },
    PerimeterX: { selector: '#px-captcha', success_selector: '#px-success' },
    SimpleCaptcha: { selector: '.simple-captcha', success_selector: '.captcha-done' },
    FunCaptcha: { selector: '.funcaptcha', success_selector: '.funcaptcha-success' },
    CloudflareTurnstile: { selector: '.cf-turnstile', success_selector: '.cf-success' },
    AWSWAF: { selector: '#aws-waf-captcha', success_selector: '#aws-waf-success' },
    GeeTest: { selector: '.geetest-captcha', success_selector: '.geetest-success' },
    KeyCAPTCHA: { selector: '#keycaptcha', success_selector: '#keycaptcha-success' },
    PuzzleCAPTCHA: { selector: '.puzzle-captcha', success_selector: '.puzzle-solved' },
    YandexCAPTCHA: { selector: '#yandex-captcha', success_selector: '#yandex-success' },
    ImageCAPTCHA: { selector: '.image-captcha', success_selector: '.image-captcha-success' },
    TextCAPTCHA: { selector: '.text-captcha', success_selector: '.text-captcha-success' }
  };

  // 获取对应 CAPTCHA 类型的选择器
  const selectedOptions = captchaSelectors[captchaType] || {};

  // 将默认选项、该 CAPTCHA 类型的选项和自定义选项合并
  return { ...defaultOptions, ...selectedOptions, ...customOptions };
}

// 不同 CAPTCHA 类型的示例用法
const ddOptions = getCaptchaOptions('DataDome', { timeout: 40000, debug: true });
const recaptchaOptions = getCaptchaOptions('reCAPTCHA', { debug: true });
const hcaptchaOptions = getCaptchaOptions('hCaptcha');

console.log(ddOptions);
console.log(recaptchaOptions);
console.log(hcaptchaOptions);

// 示例错误处理
try {
  if (!document.querySelector(ddOptions.selector)) {
    throw new Error(`无法通过选择器找到 CAPTCHA 元素: ${ddOptions.selector}`);
  }

  // 在此编写你的 CAPTCHA 求解逻辑
  solveCaptcha(ddOptions);
} catch (error) {
  console.error('求解 CAPTCHA 失败:', error.message);
}
```

#### 示例流程：  
1. **检测 CAPTCHA**：求解器识别 CAPTCHA 类型（如 PerimeterX）。  
2. **求解 CAPTCHA**：使用 AI 逻辑自动完成校验。  
3. **失败重试**：若求解失败，系统会自动更换 IP 并重试。  
4. **返回结果**：成功后，系统可无缝访问目标站点。  

## 支持的 CAPTCHA 类型

Bright Data 的 CAPTCHA 求解器适配多种类型的 CAPTCHA，包括：

- [**DataDome**](https://www.bright.cn/products/web-unlocker/captcha-solver/datadome)
- [**reCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/recaptcha)
- [**Click Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/click-captcha)
- [**Cloudflare**](https://www.bright.cn/products/web-unlocker/captcha-solver/Cloudflare)
- [**PerimeterX**](https://www.bright.cn/products/web-unlocker/captcha-solver/perimeterx)
- [**SimpleCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)
- [**FunCaptcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/funcaptcha)
- [**Cloudflare Turnstile**](https://www.bright.cn/products/web-unlocker/captcha-solver/cloudflare-turnstile)
- [**AWS WAF Captcha**](https://www.bright.cn/products/web-unlocker/captcha-solver/aws-waf-captcha)
- [**GeeTest CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/geetest-captcha)
- [**KeyCAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/keycaptcha)
- [**Puzzle CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/puzzle-captcha)
- [**Yandex CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/yandex-captcha)
- [**Image CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/image-captcha)
- [**Text CAPTCHA**](https://www.bright.cn/products/web-unlocker/captcha-solver/text-captcha)

## 高级自定义

[Bright Data 的 CAPTCHA 求解器](https://github.com/bright-cn/Captcha-solver) 支持高级自定义，针对特定场景可对求解逻辑进行精确微调。

## **事件监控**  
追踪 CAPTCHA 求解事件，以应对高级用例：  
- `Captcha.detected`: 检测到 CAPTCHA 并开始求解  
- `Captcha.solveFinished`: 成功求解 CAPTCHA  
- `Captcha.solveFailed`: 求解 CAPTCHA 失败  

## **价格方案**

| **方案**               | **价格 (每 1K 结果)** | **月度费用**        | **说明**                                 |  
|-----------------------|-----------------------|--------------------|------------------------------------------|  
| **按量付费**           | $1.50                | 无固定承诺         | 适合临时/不定期的爬取需求                |  
| **Growth**            | $1.27                | $499               | 为扩张中的团队定制                       |  
| **Business**          | $1.12                | $999               | 适合大规模爬取数据场景                   |  
| **Premium**           | $1.05                | $1,999             | 高级功能及优先支持                       |  
| **Enterprise**        | 自定义报价           | 联系我们           | 面向大型企业的定制解决方案               |  

🚀 **特别优惠**：首次充值最高可获得与充值额等额的配套金额（上限 **$500**）！

## **开发者为何喜爱 SimpleCaptcha 求解器**  
- **集成简单**：与 Puppeteer、Playwright、Selenium 无缝配合使用。  
- **先进的 AI 求解逻辑**：自动处理重试、CAPTCHA 求解、指纹模拟、IP 轮换和请求头等。  
- **内置浏览器**：无需额外管理外部浏览器来处理 JavaScript。  
- **实时洞察**：通过实时监控面板查看网络性能。  
- **卓越支持**：全球 24/7 客户支持，每日迭代添加新功能。  

## **常见问题**

### **SimpleCaptcha 求解器如何工作？**  
该求解器利用 AI 逻辑自动检测并求解 SimpleCaptcha。

### **可以同时处理多个 CAPTCHA 吗？**  
可以。该解决方案支持并发处理多种 CAPTCHA，确保访问不中断。

### **若 CAPTCHA 求解失败怎么办？**  
系统会自动重试。如仍有问题，可随时联系我们 24/7 的支持团队寻求帮助。

---

## **告别 SimpleCaptcha 的困扰**  
立即开始免费试用，体验 Bright Data 提供的流畅 [SimpleCaptcha 求解](https://www.bright.cn/products/web-unlocker/captcha-solver/simplecaptcha)！
