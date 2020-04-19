---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219890"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Microsoft 固有の仕様**

コンピューターの変換の検索用バッファーのアドレスマッピングエントリを無効にします。 無効にするページの仮想アドレスとアドレス空間識別子をパラメーターで指定します。

## <a name="syntax"></a>構文

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>パラメーター

*Vaddr*\
から無効化するページの仮想アドレス。

*as_id*\
から無効化するページのアドレス空間識別子 (ASID)。

## <a name="remarks"></a>Remarks

`__svm_invlpga` 関数は `INVLPGA` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:システムプログラミング、 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイトの「ドキュメント番号24593、リビジョン3.11」。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_invlpga`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
