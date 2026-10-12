# 2026-10 北京地铁官方时刻表存档

- 来源文件写入时间：2026-10-11 16:00–17:02（Asia/Shanghai；文件时间戳）。项目索引于 18:27 以离线 `rebuild` 模式生成。
- 来源：北京地铁官网、北京京港地铁、京投轨道运营。未包含第三方 community 数据。
- `raw/` 保存官方原始 API JSON、HTML 与时刻表原图。
- `processed/first_last.jsonl` 是 1,722 条首末车记录；`processed/bjsubway_departures.jsonl` 是官网 1,440 张时刻表图片的 OCR 分钟表；`processed/official_timetable_images.jsonl` 建立官方图片与元数据的对应。
- `processed/bjsubway_review_queue.jsonl` 标出 OCR 不确定项及格式异常。结构校验不等同于逐项人工对图。首末班源数据字段缺失记录见 `processed/first_last_review_queue.jsonl`。
- 京投图片记录在 `processed/bjmoa_review_queue.jsonl`；本次 OCR 未能读取这些图片，仍须人工对图转录。
- `processed/acquisition_index.json` 是去除本机绝对路径后的采集摘要。注意：索引 `ocr_parsed=0`，但 OCR 缓存实有 1,440 条；本月转录基于该缓存。原缓存见 `processed/bjsubway_ocr_results.jsonl`。
- `processed/sha256_manifest.jsonl` 为原始文件的 SHA-256 与字节数清单。
- 校验汇总见 `processed/verification_report.json`。

字段和每月流程见仓库根目录 `README.md`。

## 独立二级分析

二级结果见 [analysis/README.md](analysis/README.md)，以本月原始 JSON、HTML、图片重新计算，不使用既有 OCR 结果。包含小时/时段计数、工作日与双休日比、代表站及相邻站差异、单图图例对应的小交路候选、首末车跨度和异常队列。该月是首次比较基线，暂无历史变化结论。图像自动检查通过仍需区别于完整人工复核，详情见分析校验与固定样本记录。
