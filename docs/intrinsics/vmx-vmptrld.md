---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219496"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Microsoft 固有の仕様**

指定されたアドレスから、現在の仮想マシンの制御構造 (VMCS) へのポインターを読み込みます。

## <a name="syntax"></a>構文

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>パラメーター

*Vmcsphysのアドレス*\
からVMCS ポインターが格納されているアドレス。

## <a name="return-value"></a>戻り値

0\
操作が成功しました。

1\
現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。

2\
有効な状態がないため操作は失敗しました。

## <a name="remarks"></a>Remarks

VMCS ポインターは、64ビットの物理アドレスです。

`__vmx_vmptrld` 関数は `VMPTRLD` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)サイトのドキュメント「IA-32 intel Architecture の Intel Virtualization Technical Specification」 (ドキュメント番号 C97063-002) を検索してください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
