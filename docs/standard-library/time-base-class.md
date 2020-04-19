---
title: time_base クラス
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685790"
---
# <a name="time_base-class"></a>time_base クラス

クラスは、列挙型 `dateorder` とこの型のいくつかの定数を定義するクラステンプレート time_get のファセットの基底クラスとして機能します。

## <a name="syntax"></a>構文

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>Remarks

各定数は、日付部分を順序付けるための異なる方法を特徴付けます。 定数は次のとおりです。

- `no_order` は特定の順序を指定しません。

- `dmy` は、1979年12月2日のように、日、月、年の順序を指定します。

- `mdy` は、1979年12月2日に示すように、月、日、年の順序を指定します。

- `ymd` は、1979/12/2 のように、年、月、日の順に指定します。

- `ydm` は、1979: 2 Dec のように、年、日、月を指定します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
