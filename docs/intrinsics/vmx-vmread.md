---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219436"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Microsoft 固有の仕様**

現在の仮想マシン制御構造 (VMCS) から指定されたフィールドを読み取り、指定された場所に配置します。

## <a name="syntax"></a>構文

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>パラメーター

*分野*\
から読み取る VMCS フィールド。

*FieldValue*\
から`Field`パラメーターで指定した vmcs フィールドから読み取った値を格納する場所へのポインター。

## <a name="return-value"></a>戻り値

|値|説明|
|-----------|-------------|
|0|操作が成功しました。|
|1|現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。|
|2|有効な状態がないため操作は失敗しました。|

## <a name="remarks"></a>Remarks

`__vmx_vmread` 関数は `VMREAD` マシン語命令と同じです。 `Field`パラメーターの値は、Intel のドキュメントで説明されているエンコードされたフィールドインデックスです。 詳細については、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)のサイトの「IA-32 intel アーキテクチャの Intel Virtualization Technical Specification」を参照してください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmread`|X64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
