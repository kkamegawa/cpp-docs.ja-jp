---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219394"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Microsoft 固有の仕様**

現在の仮想マシン制御構造 (VMCS) 内の指定されたフィールドに、指定された値を書き込みます。

## <a name="syntax"></a>構文

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>パラメーター

*分野*\
から書き込む VMCS フィールド。

*FieldValue*\
からVMCS フィールドに書き込む値。

## <a name="return-value"></a>戻り値

0\
操作が成功しました。

1\
現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。

2\
有効な状態がないため操作は失敗しました。

## <a name="remarks"></a>Remarks

`__vmx_vmwrite` 関数は `VMWRITE` マシン語命令と同じです。 `Field`パラメーターの値は、Intel のドキュメントで説明されているエンコードされたフィールドインデックスです。 詳細については、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)のサイトの「IA-32 intel アーキテクチャの Intel Virtualization Technical Specification」を参照してください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
