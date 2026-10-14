# 更低成本的 ArtCraft 图片素材方案

## 输入

[Original prompts and parameters](cases/briefs.json)

## 生成与输出

独立 ToAPIs 素材脚本完成文生图与参考改图；提供 PNG 和参数清单供导入，ArtCraft 画布导入与原生 Provider 未验收。

逐案例执行；生成后保存原 PNG 与 SHA256。参考案例依赖首张图；先生成或复用首张图，再执行参考编辑。不要删除 private-state 后重跑同一任务。

## ArtCraft 导入路径（待产品内验收）

先从原脚本获得 3 个 PNG；用最新 ArtCraft 的图片上传/导入入口选中本地 PNG，再将其作为图层/参考素材。入口名称以版本为准。该手动流程依据上游图片导入/上传代码准备，本轮没有启动其桌面画布，因此不能称作原生 ToAPIs Provider。正式 Provider 需要另接凭据、模型目录、费用估计、任务轮询、上传与结果事件。

## 参数与截图

[Exact request evidence](evidence/runs.json) · [Original outputs](assets/)

README 中的双语封面由原图与脱敏请求信息制作，不是上游软件 UI 截图。
