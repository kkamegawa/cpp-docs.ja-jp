---
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: da6ca9786b9c7e5041b9a8ca908d567b16176436
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219817"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Microsoft 固有の仕様**

指定されたバーチャルマシン制御ブロック (VMCB) からプロセッサ状態のサブセットを読み込みます。

## <a name="syntax"></a>構文

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>パラメーター

*VmcbPhysicalAddress*\
からVMCB の物理アドレス。

## <a name="remarks"></a>Remarks

`__svm_vmload` 関数は `VMLOAD` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:システムプログラミング、 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイトの「ドキュメント番号24593、リビジョン3.11」。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_vmload`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
