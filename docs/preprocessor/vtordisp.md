---
title: vtordisp プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 3c676ab2bfee1b6cf3caff3ab456a4f23f2744c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216481"
---
# <a name="vtordisp-pragma"></a>vtordisp プラグマ

**C++のみ**

非表示`vtordisp`の構築/破棄のディスプレイスメントメンバーの追加を制御します。

## <a name="syntax"></a>構文

> **#pragma vtordisp (** **[プッシュ,]** *n* **)** \
> **#pragma vtordisp (pop)** \
> **#pragma vtordisp ()** \
> **#pragma vtordisp (** **[プッシュ,]** { **on** | **off** } **)**

### <a name="parameters"></a>パラメーター

**押し付け**\
現在`vtordisp`の設定を内部コンパイラスタックにプッシュし、新しい`vtordisp`設定を*n*に設定します。  *N*が指定されてい`vtordisp`ない場合、現在の設定は変更されません。

**ショート**\
内部コンパイラスタックから上位レコードを削除し、削除され`vtordisp`た値に設定を復元します。

*n*\
`vtordisp`設定の新しい値を指定します。 使用可能な値は`/vd0`、、 `/vd1`、および`/vd2`コンパイラオプションに対応する0、1、または2です。 詳細については、「 [/vd (コンストラクションの変位の無効化)](../build/reference/vd-disable-construction-displacements.md)」を参照してください。

**代わっ**\
これは、`#pragma vtordisp(1)` に相当します。

**オート**\
これは、`#pragma vtordisp(0)` に相当します。

## <a name="remarks"></a>Remarks

**Vtordisp**プラグマは、仮想ベースを使用するコードにのみ適用できます。 派生クラスが仮想基底クラスから継承する仮想関数をオーバーライドする場合、および派生クラスのコンストラクターやデストラクターが仮想基底クラスへのポインターを使用してその関数を呼び出す場合、コンパイラは仮想基底クラスを含むクラスに追加の `vtordisp` 隠しフィールドを導入する場合があります。

**Vtordisp**プラグマは、その後に続くクラスのレイアウトに影響します。 、 `/vd0` 、`/vd1`および`/vd2`の各オプションでは、モジュール全体で同じ動作を指定します。 0または**off**を指定する`vtordisp`と、非表示のメンバーが抑制されます。 クラスのコンストラクターとデストラクターが`this`ポインターによって指されたオブジェクトの仮想関数を呼び出す可能性がない場合にのみ、vtordisp をオフにします。

1または**on**(既定値) を指定する`vtordisp`と、必要に応じて非表示のメンバーが有効になります。

2を指定すると`vtordisp` 、仮想関数を持つすべての仮想ベースに対して非表示のメンバーが有効になります。  `#pragma vtordisp(2)`部分的に構築されたオブジェクトで**dynamic_cast**のパフォーマンスを正しく確保するために必要な場合があります。 詳細については、「[コンパイラの警告 (レベル 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)」を参照してください。

`#pragma vtordisp()`引数を指定せずに、 `vtordisp`設定を初期設定に戻します。

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**特定C++の終了**

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
