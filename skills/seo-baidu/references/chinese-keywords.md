# Chinese Keyword Research

Used by `/seo baidu keywords <topic>`.

## Why translation is not enough

Chinese searchers often use different terms from a literal translation of the
English keyword, and Chinese has no spaces, so Baidu segments the query into
words itself. Build the list from how Chinese users actually search, not from
a translated English list.

## Method

1. **Seed terms**: ask the user for their Chinese product and category names.
   If they have none, propose candidates and mark them unverified.
2. **Variants**: for each seed, list synonyms, the common short form, the
   formal term, and brand plus category combinations. Watch for terms that
   differ between mainland and Taiwan or Hong Kong usage.
3. **Demand**: Baidu Index (百度指数, index.baidu.com) gives relative search
   trends, not absolute volumes, and needs a Baidu account. Baidu's own
   autocomplete (下拉框) and related searches (相关搜索) at the bottom of the
   SERP show real phrasing. Paid volume data comes from Baidu's advertising
   keyword planner (关键词规划师) or third-party tools such as 5118 and
   Aizhan (爱站); say which source each number came from.
4. **Intent**: classify each term as informational, commercial,
   transactional or navigational, as in `seo-cluster`.
5. **SERP check**: for the top terms, note how much of page one Baidu's own
   properties (Baike, Zhidao, Baijiahao, Wenku) take. A term where they hold
   most of page one is better won by publishing on those properties than by
   ranking the site.
6. **Wording check**: drop or rewrite terms that use banned absolute claims
   (最, 第一, 顶级, 国家级, 绝对) before they reach titles.

## Output

| Keyword | Pinyin | English gloss | Intent | Demand (source) | Baidu-owned share of page 1 | Target page |
|---------|--------|---------------|--------|-----------------|-----------------------------|-------------|

Mark every demand figure with its source, and every figure Claude could not
fetch as **unverified**.
