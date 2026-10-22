# BatchRenamer 落地页

纯静态单文件，无外部依赖（无 CDN、无外部字体、无外部脚本 —— 实测 `<script src=>`、`<link rel=stylesheet>`、`<img src=>` 均为 0 处）。
真实浏览器渲染已验证：0 控制台报错，截图见 `_render-verified.png`。

## 部署（GitHub Pages）
把本目录内容推到 `gh-pages` 分支（或 main 分支的 `/docs` 目录），
然后在仓库 Settings → Pages 里选择对应来源即可。

## 上架后要改的地方

`index.html` 第 450 行：

```js
var GUMROAD_URL = "PLACEHOLDER_REPLACE_WITH_YOUR_GUMROAD_URL";
```

把 `PLACEHOLDER_...` 换成真实的商品链接。未替换时点购买按钮会弹出提示，
不会跳到坏链接。

> ⚠️ **变量名是历史遗留**（原计划挂 Gumroad）。现在主通道已改为 **itch.io**
> （原因：Gumroad 出款依赖 Stripe Connect，而 Stripe 可用国家列表不含中国大陆；
> itch.io 官方明确支持 PayPal / Payoneer 出款）。
> 变量名可以不改，填 itch.io 的商品页 URL 即可；若要改，三处一起改
> （L450 定义、L452 判断、L453 赋值）。

## 上架前仍需人工处理
- 截图加红框标注（`04-product/docs/screenshot-*.png` 是原始界面图）
- 裁 16:9 封面图
- 替换上面的商品链接
