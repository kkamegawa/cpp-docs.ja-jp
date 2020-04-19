---
title: money_base クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689325"
---
# <a name="money_base-class"></a>money_base クラス

クラスは、クラステンプレート[moneypunct](../standard-library/moneypunct-class.md)のすべての特殊化に共通する列挙型と構造体を記述します。

## <a name="syntax"></a>構文

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Remarks

列挙 `part` は、構造パターンの配列フィールドの要素で使用可能な値を示します。 @No__t_0 の値は次のとおりです。

- 0個以上の空白に一致する `none`、または何も生成しません。

- 正または負の符号を一致または生成する `sign` ます。

- 0個以上の空白に一致する `space`、またはスペースを生成します。

- 通貨記号を一致または生成する `symbol` ます。

- 通貨値の一致または生成を `value` します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
