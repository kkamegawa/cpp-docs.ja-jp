---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219540"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Microsoft 固有の仕様**

指定された仮想マシン制御構造 (VMCS) を初期化し、その`Clear`起動状態をに設定します。

## <a name="syntax"></a>構文

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>パラメーター

*Vmcsphysのアドレス*\
から消去する VMCS の物理アドレスを格納している64ビットメモリ位置へのポインター。

## <a name="return-value"></a>戻り値

|値|説明|
|-----------|-------------|
|0|操作が成功しました。|
|1|現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。|
|2|有効な状態がないため操作は失敗しました。|

## <a name="remarks"></a>Remarks

アプリケーションでは、 [__ vmxvmlaunch](../intrinsics/vmx-vmlaunch.md)関数または[__ vmx_l](../intrinsics/vmx-vmresume.md)関数のいずれかを使用して、VM 入力操作を実行できます。 [__ Vmxvmlaunch](../intrinsics/vmx-vmlaunch.md)関数は、起動状態が`Clear`である vmcs でのみ使用できます。また、 [__ vmxvmresume](../intrinsics/vmx-vmresume.md)関数は、起動状態が`Launched`である vmcs でのみ使用できます。 そのため、VMCS の起動状態をに`Clear`設定するには、 [__ vmxvmclear](../intrinsics/vmx-vmclear.md)関数を使用します。 最初の VM 入力操作には[__ vmxvmlaunch](../intrinsics/vmx-vmlaunch.md)関数を使用し、後続の vm 入力操作には[__ vmx_l](../intrinsics/vmx-vmresume.md)関数を使用します。

`__vmx_vmclear` 関数は `VMCLEAR` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)サイトのドキュメント「IA-32 intel Architecture の Intel Virtualization Technical Specification」 (ドキュメント番号 C97063-002) を検索してください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
