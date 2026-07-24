改配置文件：vite.config.ts、tauri.conf.json、package.json 三处要一致。




编辑了文件已编辑 package.json+2-2






已编辑 tauri.conf.json+1-1











前两个配置已经改到 6173。继续同步 Vite 配置里的端口和注释。




已编辑 vite.config.ts+2-2






配置改好了。现在跑构建验证一下，然后我临时起一下 6173 看页面能不能正常返回。




已运行 pnpm --filter @publish/desktop build




构建暴露了一个前端类型问题，不是端口改动引起的：发布成功页按钮直接绑定了 reload(quiet?: boolean)，Vue 会把点击事件传进去，类型不匹配。这个会影响构建，我顺手修掉。




已运行 $lines = Get-Content -Encoding UTF8 apps/desktop/src/pages/platforms/github/GitHubPublishSuccess.vue; for ($i=50; $i -le 78; $i++) { '{0}: {1}' -f ($i+1), $lines[$i] }; for ($i=164; $i -le 176; $i++) { '{0}: {1}' -f ($i+1), $lines[$i] }




我把刷新按钮改成显式调用，不让点击事件
