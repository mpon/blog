---
title: はてなブログProを解約した
date: "2022-03-22T00:01:03.284+09:00"
description: "独自ドメインがなくなったのでなんとかしたい"
---

はてなブログProを解約したので独自ドメインがリンク切れになった。

今はRoute53でドメイン管理しているので、CloudFront+S3でCloudFrontのリダイレクトで飛ばせるのはいけそうと思ってたけど、e34.fmでCloudFlare Pagesが良さそうみたいのを聞いていて試したいと思ってた。

ドメイン管理もRoute53からCloudFlareに移行すればPage Ruleでリダイレクト行けるとは思うんだけど、CloudFlareは無料プランで一旦は行きたいから、ドメイン管理は移行したくなかった。

どうやらそうすると、Page Ruleは使えなさそうだった（それはそう）。

どうしようかなって思ってたところ、CloudFlareにはBulk Redirectsという仕組みがあるみたいでそれを使うだけでいけてしまった。

```
source_url: www.mpon.me/entry
target_url: https://mpon.hatenablog.com/entry
preserve_path_suffix: true
```

これで、https://www.mpon.me/entry/2020/12/31/213933 が https://mpon.hatenablog.com/entry/2020/12/31/213933 にリダイレクトされるようになった。
