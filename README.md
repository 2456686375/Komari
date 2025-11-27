<h1>Komari Glass Theme</h1>

<p>
  一个基于 <strong>Vite + React + TypeScript + Tailwind CSS + shadcn 风格组件</strong> 的 Komari Monitor 主题。<br>
  特点：紫蓝渐变背景、50px 玻璃模糊、大卡片布局、卡片 / 表格双视图、深浅色切换。
</p>

<hr>

<h2>功能特性</h2>

<ul>
  <li>
    🎨 <strong>玻璃拟态 UI</strong>
    <ul>
      <li>主体容器使用 <code>backdrop-filter: blur(50px)</code> 配合渐变背景。</li>
      <li>圆角 + 软阴影 + 紫蓝科技风配色。</li>
    </ul>
  </li>
  <li>
    🖥 <strong>节点展示</strong>
    <ul>
      <li>支持 <strong>卡片视图</strong> 和 <strong>表格视图</strong> 一键切换。</li>
      <li>卡片中展示 CPU / 内存 / 磁盘 / 网络等基础状态。</li>
      <li>表格视图展示名称 / 分组 / 位置 / 配置 / 系统 / 磁盘等信息。</li>
    </ul>
  </li>
  <li>
    🧩 <strong>Komari 官方 API 兼容</strong>
    <ul>
      <li>使用 <code>/api/public</code> 拉取站点信息与 <code>theme_settings</code>。</li>
      <li>使用 <code>/api/nodes</code> 拉取节点列表。</li>
      <li>使用 <code>/api/recent/{uuid}</code> 拉取单个节点近期数据（CPU / 内存 / 磁盘 / 网络）。</li>
    </ul>
  </li>
  <li>
    ⚙️ <strong>主题设置（komari-theme.json -&gt; theme_settings）</strong>
    <ul>
      <li><code>accent_color</code>：主色调（紫色 / 蓝色 / 粉色 / 青色）。</li>
      <li><code>show_price</code>：是否在卡片中显示价格信息。</li>
      <li><code>show_ping_chart</code>：预留选项，将来可扩展为详细图表页。</li>
    </ul>
  </li>
  <li>
    🌗 <strong>深浅色切换</strong>
    <ul>
      <li>自定义 <code>ThemeProvider</code>，支持 <code>light / dark / system</code>。</li>
      <li>使用 <code>localStorage.appearance</code> 存储外观，兼容 Komari 推荐习惯。</li>
    </ul>
  </li>
  <li>
    🧭 <strong>状态记忆</strong>
    <ul>
      <li>分组选择：<code>nodeSelectedGroup</code>。</li>
      <li>视图模式：<code>nodeViewMode</code>（grid / table）。</li>
      <li>外观模式：<code>appearance</code>（light / dark / system）。</li>
    </ul>
  </li>
</ul>

<hr>

<h2>技术栈</h2>

<ul>
  <li><a href="https://vitejs.dev/" target="_blank" rel="noreferrer">Vite</a> + React + TypeScript</li>
  <li><a href="https://tailwindcss.com/" target="_blank" rel="noreferrer">Tailwind CSS</a></li>
  <li>shadcn 风格 UI 组件（Button / Card 等封装在 <code>src/components/ui</code>）。</li>
  <li><a href="https://lucide.dev/" target="_blank" rel="noreferrer">lucide-react</a> 图标。</li>
</ul>

<hr>

<h2>项目结构</h2>

<pre><code>komari-glass-theme/
├── komari-theme.json        # Komari 主题配置（必须）
├── index.html               # 入口 HTML（必须保持 title/description 原文）
├── package.json
├── vite.config.ts
├── tailwind.config.ts
├── tsconfig.json
├── README.md
└── src/
    ├── App.tsx              # 主题主界面（卡片视图 / 表格视图）
    ├── main.tsx             # React 入口
    ├── index.css            # Tailwind + 全局样式（含玻璃拟态容器）
    ├── lib/
    │   └── utils.ts         # cn() 工具函数
    └── components/
        ├── theme-provider.tsx  # 主题切换 Provider，保存到 localStorage
        ├── mode-toggle.tsx     # 深浅色切换按钮
        └── ui/
            ├── button.tsx      # Button 组件（shadcn 风格）
            └── card.tsx        # Card 组件（shadcn 风格）
</code></pre>

<hr>

<h2>开发环境要求</h2>

<ul>
  <li>Node.js &gt;= 18</li>
  <li>推荐使用 <code>pnpm</code>（也可以使用 npm / yarn，自行替换命令）。</li>
</ul>

<hr>

<h2>本地开发</h2>

<p>安装依赖：</p>

<pre><code>pnpm install
</code></pre>

<p>启动开发服务器：</p>

<pre><code>pnpm dev
</code></pre>

<p>默认访问地址：</p>

<pre><code>http://localhost:5173
</code></pre>

<p>
  如果想看到真实数据，需要有一个已部署的 Komari 后端，并且当前前端可以访问 <code>/api/public</code>、
  <code>/api/nodes</code>、<code>/api/recent/{uuid}</code>。
</p>

<hr>

<h2>构建生产版本</h2>

<p>构建：</p>

<pre><code>pnpm build
</code></pre>

<p>构建完成后会生成：</p>

<pre><code>dist/
  ├── index.html
  ├── assets/...
  └── ...
</code></pre>

<hr>

<h2>打包为 Komari 主题</h2>

<p>一个可用的 Komari 主题 zip 至少需要包含：</p>

<ul>
  <li><code>komari-theme.json</code></li>
  <li><code>dist/</code>（整个 Vite 构建输出目录）</li>
  <li><code>preview.png</code>（可选，用于后台预览缩略图）</li>
</ul>

<p>推荐打包结构示例：</p>

<pre><code>KomariGlass.zip
└── KomariGlass/
    ├── komari-theme.json
    ├── preview.png        # 可选
    └── dist/
        ├── index.html
        ├── assets/...
        └── ...
</code></pre>

<p><strong>上传步骤：</strong></p>
<ol>
  <li>登录 Komari 面板后台。</li>
  <li>打开「主题 / Themes」页面。</li>
  <li>选择「上传主题」或「本地上传」。</li>
  <li>选择打包好的 zip，并确认导入。</li>
  <li>在主题列表中启用 Komari Glass Theme。</li>
</ol>

<hr>

<h2>与 Komari 的交互说明</h2>

<h3>使用的 API</h3>

<ul>
  <li>
    <code>GET /api/public</code><br>
    返回站点名称、描述、当前启用主题以及 <code>theme_settings</code> 等。
  </li>
  <li>
    <code>GET /api/nodes</code><br>
    返回所有节点的基础信息（名称、分组、CPU、区域等）。
  </li>
  <li>
    <code>GET /api/recent/{uuid}</code><br>
    返回对应节点最近一段时间的数据（这里取数组第一个点用于实时状态展示）。
  </li>
</ul>

<p>
  如果你的后端路径有前缀（例如 <code>/komari/api/...</code>），请在前端代码中将
  <code>fetch("/api/xxx")</code> 相应改成 <code>fetch("/komari/api/xxx")</code>。
</p>

<h3>使用的 localStorage Key</h3>

<ul>
  <li><code>appearance</code>：当前外观（light / dark / system）。</li>
  <li><code>nodeSelectedGroup</code>：节点分组筛选。</li>
  <li><code>nodeViewMode</code>：视图模式（grid / table）。</li>
</ul>

<hr>

<h2>自定义与二次开发</h2>

<ul>
  <li>
    <strong>玻璃模糊强度</strong><br>
    编辑 <code>src/index.css</code> 中的 <code>.glass-panel</code>：
    <pre><code>.glass-panel {
  /* ...其他样式... */
  backdrop-filter: blur(50px); /* 在这里调整模糊强度 */
}
</code></pre>
  </li>
  <li>
    <strong>主色渐变</strong><br>
    在 <code>App.tsx</code> 的 <code>accentGradient()</code> 中，修改不同 <code>accent_color</code> 对应的
    Tailwind 渐变类（如改成更偏粉色 / 蓝色）。
  </li>
  <li>
    <strong>显示更多字段</strong><br>
    想展示 GPU、虚拟化类型等信息，可以直接在 <code>NodeCard</code> 或 <code>NodeTable</code> 中
    增加对应字段的渲染即可。
  </li>
</ul>

<hr>

<h2>License</h2>

<p>
  本主题示例主要用于自用与学习，如需商用或二次分发，请根据自身需求补充 License 说明。
</p>
