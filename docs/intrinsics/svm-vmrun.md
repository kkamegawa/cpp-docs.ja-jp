---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219822"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Microsoft 固有の仕様**

指定された仮想マシン制御ブロック (VMCB) に対応する仮想マシンのゲストコードの実行を開始します。

## <a name="syntax"></a>構文

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>パラメーター

*VmcbPhysicalAddress*\
からVMCB の物理アドレス。

## <a name="remarks"></a>Remarks

関数`__svm_vmrun`は、仮想マシンのゲストコードの実行を開始するために、vmcb 内の最小限の情報を使用します。 複雑な割り込みを処理したり、別のゲストに切り替えたりするための情報を追加する必要がある場合は、 [__ svmvmsave](../intrinsics/svm-vmsave.md)または[__ svmの vmload](../intrinsics/svm-vmload.md)関数を使用します。

`__svm_vmrun` 関数は `VMRUN` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイトでのシステムプログラミング、"ドキュメント番号24593、リビジョン3.11 以降。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_vmrun`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
