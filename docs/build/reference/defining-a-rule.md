---
title: 規則の定義
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: cd82dc5b0693e563fd3d75a0215265089ff57913
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342894"
---
# <a name="defining-a-rule"></a>規則の定義

*Fromext*依存のファイルの拡張機能を表すと*toext*ターゲット ファイルの拡張子を表します。

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Remarks

拡張は、大文字小文字が区別されていません。 表すマクロを呼び出すことができる*fromext*と*toext*; マクロは、プリプロセス時に展開されます。 上記ピリオド (.) *fromext*行の先頭に置く必要があります。 コロン (:) は、スペースまたはタブの 0 個以上続きます。 これは、スペースまたはタブ、コマンドを指定するにはセミコロン (;)、番号記号 (#)、コメントを指定して、または改行文字によってのみ実行できます。 その他の空白は許可されません。 記述ブロックのように、コマンドが指定されます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[規則の検索パス](search-paths-in-rules.md)

## <a name="see-also"></a>関連項目

[推論規則](inference-rules.md)
