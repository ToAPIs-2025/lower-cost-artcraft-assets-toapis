# Lower-cost ArtCraft image assets

[中文](README_zh-CN.md)

ToAPIs `gpt-image-2-vip / low / 1K / n=1` for ArtCraft workflows. 3 image-2(vip) images: **$0.0057 actually charged**.

External ToAPIs asset script validates generation and reference edits. PNGs and parameter manifests are ready for import; ArtCraft canvas import and native providers remain untested.

> Community tutorial; no upstream endorsement. “Lower-cost” describes this API tier, not total software or all-model costs.

## Demo

![API case overview](assets/overview-en.png)

| Case | Original image | Output pixels |
|---|---|---|
| 01-cabin | [PNG](assets/01-cabin.png) | 1536 × 864 |
| 02-dawn | [PNG](assets/02-dawn.png) | 1536 × 864 |
| 03-night | [PNG](assets/03-night.png) | 1536 × 864 |

## Model price and this demo’s cost

| Model | Configuration | API unit quote |
|---|---|---|
| `gpt-image-2-vip` | `low / 1K / n=1` | **$0.0019** |

3 image-2(vip) images: **$0.0057 actually charged**。

[API pricing snapshot](evidence/pricing.json) · [Cost record](evidence/costs.json) · [Original requests](evidence/runs.json)

Quote checked on 2026-10-14. Other tiers, resolutions, models, agents and machine costs are excluded.

[ToAPIs model landing page](https://go2v.toapis.com/1014_artcraft_lowercost_gh_en)

## Reproduce

Set `TOAPIS_API_KEY` privately in your local environment. Keep it out of source code and chats. Use `TOAPIS_BASE_URL=https://toapis.cn` or `https://toapis.com`.


```bash
# Inspect without paid calls
python scripts/run_demo.py
# Generate the original cases (charged; exact quote checked first)
python scripts/run_demo.py --live --output results
```

The generic script is an external asset runner. Original PPT Master CLI runs are separately identified in the evidence.

## API mapping

```text
Authorization: Bearer TOAPIS_API_KEY
POST /v1/uploads/images             # reference PNG -> HTTPS URL
POST /v1/images/generations         # model,prompt,size,resolution,quality,n,reference_images
GET  /v1/images/generations/{id}    # poll the SAME task
completed -> result.data[0].url -> download PNG without the API key
```

Generation POST is never automatically retried. Preserve .toapis-state or results/private-state to resume the same task. Reference editing is not masked inpainting. Masks, transparency, audio and cloud video were not tested.

## Upstream and licenses

[storytold/artcraft](https://github.com/storytold/artcraft) · [pinned `d4e4ac69`](https://github.com/storytold/artcraft/tree/d4e4ac69bbd93d237eaf5d0260bc6a5ff3a5e373)

[Third-party notices](THIRD_PARTY_NOTICES.md)
