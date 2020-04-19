---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 8bcc925b34118630c872a0147b93291626b7c19b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318603"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Remarks

このオプションは、セクションのオブジェクト ファイルがコンパイルまたはリンク時に設定された属性、セクションの属性を変更します。

コロンの後に ( **:** )、指定、*名前*セクションの。 セクション名を変更するには、次の*名前*は等号 (=) で、 *newname*セクション。

設定または変更、セクションの`attributes`、コンマ区切り (**、**) の後ろに 1 つまたは複数の属性の文字。 属性を否定するには、前に感嘆符 (!) には、その文字を付けます。 次の文字は、メモリの属性を指定します。

|属性|設定|
|---------------|-------------|
|c|code|
|d|破棄できます。|
|e|executable|
|i|初期化されたデータ|
|k|キャッシュされた仮想メモリ|
|m|リンクを削除します。|
|o|リンク情報|
|p|ページの仮想メモリ|
|r|読み取り|
|s|shared|
|u|初期化されていないデータ|
|週|書き込み|

コントロールに*配置*、文字を指定して**A**続けて次のように、(バイト単位) の配置のサイズを設定するのには、次の文字のいずれか。

|文字|配置のサイズ (バイト単位)|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|合わせなし|

指定、`attributes`と*配置*文字として空白を含む文字列。 文字では大文字小文字が区別されません。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)
