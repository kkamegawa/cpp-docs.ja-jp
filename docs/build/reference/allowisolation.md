---
title: /ALLOWISOLATION
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
ms.openlocfilehash: 359a68d5ec0a8c7390b5f0343530864e880a057c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493126"
---
# <a name="allowisolation"></a>/ALLOWISOLATION

マニフェスト検索の動作を指定します。

## <a name="syntax"></a>構文

```

/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Remarks

また、オペレーティングシステムはマニフェストの参照と読み込みを実行します。

これが既定値です。

または、 **[いいえ]** に設定すると、実行可能ファイルがマニフェストがないかのように読み込まれ、 [EDITBIN 参照](editbin-reference.md)によって省略可能`DllCharacteristics`なヘッダーのフィールドにビットが`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`設定されます。

実行可能ファイルの分離が無効の場合、Windows ローダーは、新しく作成されたプロセスに対応するアプリケーション マニフェストの検索を試行しません。 新しいプロセスには、実行可能ファイル自体にマニフェストがある場合や、*実行可能ファイル*という名前のマニフェストがある場合でも、既定のアクティベーションコンテキストがありません。

## <a name="see-also"></a>関連項目

[EDITBIN オプション](editbin-options.md)<br/>
[/ALLOWISOLATION (マニフェスト検索)](allowisolation-manifest-lookup.md)<br/>
[マニフェストファイルのリファレンス](/windows/win32/SbsCs/manifest-files-reference)
