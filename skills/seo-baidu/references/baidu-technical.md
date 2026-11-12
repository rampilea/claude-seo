# Baidu Technical Reference

Facts the seo-baidu audit checks against. Baidu changes its tools and
announces algorithms in Chinese on its own platform; verify anything that
looks out of date at ziyuan.baidu.com before reporting it as a rule.

## Spiders

| User agent token | Role |
|------------------|------|
| `Baiduspider` | Main web crawler (PC and mobile variants) |
| `Baiduspider-render` | Renderer that executes some JavaScript |
| `Baiduspider-image` | Image search |
| `Baiduspider-video` | Video search |

Verify a real Baiduspider by reverse DNS: the host name ends in
`.baidu.com` or `.baidu.jp`, and a forward lookup returns the same IP.

## Meta Tags

```html
<html lang="zh-CN">
<meta charset="utf-8">
<meta http-equiv="Content-Language" content="zh-CN">

<!-- Responsive page serving PC and mobile from one URL -->
<meta name="applicable-device" content="pc,mobile">

<!-- Stop Baidu transcoding the page or wrapping it in Siteapp -->
<meta http-equiv="Cache-Control" content="no-transform">
<meta http-equiv="Cache-Control" content="no-siteapp">

<!-- Separate mobile site: on the PC page -->
<meta name="mobile-agent" content="format=html5;url=https://m.example.cn/page">
<!-- and on the mobile page -->
<meta name="applicable-device" content="mobile">
<link rel="canonical" href="https://www.example.cn/page">
```

`<meta name="baidu-site-verification" content="...">` is the platform's
HTML-tag verification method; its presence shows the site is verified.

## Baidu Search Resource Platform (百度搜索资源平台)

| Tool | Chinese name | Use |
|------|--------------|-----|
| Site verification | 站点验证 | File, meta tag or CNAME |
| Normal indexing | 普通收录 | Sitemap submission and API push of new URLs |
| Fast indexing | 快速收录 | Quota-based priority crawl, only for eligible sites |
| Crawl diagnosis | 抓取诊断 | Fetch a URL as Baiduspider from Baidu's side |
| Crawl frequency | 抓取频次 | View and adjust crawl rate |
| robots tool | robots | Test robots.txt against Baiduspider |
| Dead links | 死链提交 | Submit removed URLs for faster dropping |
| Index volume | 索引量 | Indexed page count (the reliable number) |
| Site migration | 网站改版 | Redirect rules for domain or URL changes |

Sitemap limits used by Baidu: 50,000 URLs and 10 MB per file; use a sitemap
index for more.

## Named Algorithms

Baidu names its quality algorithms. The commonly cited ones, by what they
target:

| Name | Pinyin | Targets |
|------|--------|---------|
| 飓风 | Jùfēng (Hurricane) | Scraped, spliced or low-quality aggregated content |
| 清风 | Qīngfēng (Breeze) | Misleading titles, keyword-stuffed titles, fake downloads |
| 细雨 | Xìyǔ (Drizzle) | B2B and supply-information spam in titles and body |
| 惊雷 | Jīngléi (Thunder) | Click manipulation to fake rankings |
| 蓝天 | Lántiān (Blue Sky) | Subdomains or folders rented to third parties |
| 劲风 | Jìnfēng (Gale) | Low-quality aggregation and search-result pages |
| 冰桶 | Bīngtǒng (Ice Bucket) | Intrusive mobile ads, pop-ups, forced app downloads |
| 石榴 | Shíliu (Pomegranate) | Pages dominated by low-quality ads |
| 极光 | Jíguāng (Aurora) | Wrong or manipulated publication timestamps |
| 绿萝 | Lǜluó (Pothos) | Link buying and selling |

Map each finding to the algorithm it would trigger, so the user can read
Baidu's own announcement for it.

## Structured Data

Baidu's rich results do not follow schema.org the way Google's do, and its
former 熊掌号 (Xiongzhanghao) structured-data program has been retired. Keep
schema.org JSON-LD for the other engines and for AI answers, but do not
promise Baidu rich results from it.

## Blocked or Throttled Resources (flag in Category 2)

`fonts.googleapis.com`, `fonts.gstatic.com`, `ajax.googleapis.com`,
`www.google-analytics.com`, `www.googletagmanager.com`,
`www.google.com/recaptcha`, `www.youtube.com`, `connect.facebook.net`,
`platform.twitter.com`, `www.instagram.com`. Treat any other host as unknown
rather than blocked unless the user has mainland test data.

## Analytics

Baidu Tongji (`hm.baidu.com/hm.js`) is the common replacement for Google
Analytics, and links to the Search Resource Platform for keyword data.
