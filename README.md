# Komari
探针
里面已经包含：

komari-theme.json

index.html（符合 Komari 要求的 title/description）

vite.config.ts + tailwind.config.ts + tsconfig.json

src/

App.tsx（玻璃模糊 50px + 网格/表格视图）

main.tsx

index.css

components/theme-provider.tsx（保存到 localStorage.appearance）

components/mode-toggle.tsx

components/ui/button.tsx、components/ui/card.tsx

lib/utils.ts（cn 工具）

使用步骤简单说一下：

pnpm install
pnpm dev      # 本地预览
pnpm build    # 构建 dist/


然后把 komari-theme.json + dist/ 再压成一个 zip，上传到 Komari 主题管理即可。
