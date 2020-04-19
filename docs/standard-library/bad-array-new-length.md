---
title: bad_array_new_length クラス
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459490"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length クラス

クラスは、配列のサイズが0未満であるか、または制限を超えたために割り当て要求が成功しなかったことを示すためにスローされる例外を表します。

## <a name="syntax"></a>構文

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Remarks

によって`what`返される値は、実装定義の C 文字列です。 このメンバー関数は、いずれも例外をスローしません。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<new>

## <a name="see-also"></a>関連項目

[exception クラス](../standard-library/exception-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
