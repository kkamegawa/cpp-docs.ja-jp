---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219553"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Microsoft 固有の仕様**

現在の仮想マシン制御構造 (VMCS) を使用して、呼び出し元のアプリケーションを VMX 非ルート操作状態 (VM の入力) に配置します。

## <a name="syntax"></a>構文

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>戻り値

|値|説明|
|-----------|-------------|
|0|操作が成功しました。|
|1|現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。|
|2|有効な状態がないため操作は失敗しました。|

## <a name="remarks"></a>Remarks

アプリケーションでは、 [__ vmxvmlaunch](../intrinsics/vmx-vmlaunch.md)関数または[__ vmx_l](../intrinsics/vmx-vmresume.md)関数のいずれかを使用して、VM 入力操作を実行できます。 [__ Vmxvmlaunch](../intrinsics/vmx-vmlaunch.md)関数は、起動状態が`Clear`である vmcs でのみ使用できます。また、 [__ vmxvmresume](../intrinsics/vmx-vmresume.md)関数は、起動状態が`Launched`である vmcs でのみ使用できます。 そのため、 [__ vmxclear](../intrinsics/vmx-vmclear.md)関数を使用して vmcs の起動状態をに`Clear`設定し、最初の vm 入力操作には[__ vmx_l](../intrinsics/vmx-vmlaunch.md)関数を使用し、その後の vm には[__ vmxvmresume](../intrinsics/vmx-vmresume.md)関数を使用します。業務.

`__vmx_vmlaunch` 関数は `VMLAUNCH` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)サイトのドキュメント「IA-32 intel Architecture の Intel Virtualization Technical Specification」 (ドキュメント番号 C97063-002) を検索してください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
