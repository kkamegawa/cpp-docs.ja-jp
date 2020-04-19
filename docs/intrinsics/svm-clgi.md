---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219971"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Microsoft 固有の仕様**

グローバル割り込みフラグをクリアします。

## <a name="syntax"></a>構文

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Remarks

`__svm_clgi` 関数は `CLGI` マシン語命令と同じです。 グローバル割り込みフラグは、i/o 完了、ハードウェア温度アラート、デバッグ例外などのイベントが原因で、マイクロプロセッサが割り込みを無視、延期、または処理するかどうかを決定します。

この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:システムプログラミングについては、「 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイト」をご覧ください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_clgi`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
