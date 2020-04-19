---
title: 変更可能なデータ メンバー (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 8d592eb97f70bfc26c075317c57ec4d5c78e3956
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301592"
---
# <a name="mutable-data-members-c"></a>変更可能なデータ メンバー (C++)

このキーワードは、クラスの non-static データ メンバーおよび non-const データ メンバーにのみ適用できます。 データ メンバーが宣言されている場合**変更可能な**からこのデータ メンバーに値を代入することはその後、 **const**メンバー関数。

## <a name="syntax"></a>構文

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>Remarks

に次のコードがエラーなくコンパイルするなど、`m_accessCount`するとして宣言されている**変更可能な**で変更することができます`GetFlag`にもかかわらず`GetFlag`が const メンバー関数。

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)