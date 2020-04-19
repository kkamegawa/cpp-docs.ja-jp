---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219837"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Microsoft 固有の仕様**

グローバル割り込みフラグを設定します。

## <a name="syntax"></a>構文

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Remarks

`__svm_stgi` 関数は `STGI` マシン語命令と同じです。 グローバル割り込みフラグは、i/o 完了、ハードウェア温度アラート、デバッグ例外などのイベントが原因で、マイクロプロセッサが割り込みを無視、延期、または処理するかどうかを決定します。

この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:システムプログラミングについては、「 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイト」をご覧ください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_stgi`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
