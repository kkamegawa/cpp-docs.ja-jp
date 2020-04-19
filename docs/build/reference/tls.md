---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317264"
---
# <a name="tls"></a>/TLS

実行可能ファイルから IMAGE_TLS_DIRECTORY 構造が表示されます。

## <a name="remarks"></a>Remarks

や TLS 構造体のフィールドと TLS のコールバック関数のアドレス TLS を表示します。

プログラムではスレッド ローカル ストレージを使用しない場合、そのイメージには、TLS の構造は含まれません。  参照してください[スレッド](../../cpp/thread.md)詳細についてはします。

IMAGE_TLS_DIRECTORY は、winnt.h で定義されます。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)
