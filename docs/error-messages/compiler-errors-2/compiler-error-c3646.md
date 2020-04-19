---
title: コンパイラ エラー C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385590"
---
# <a name="compiler-error-c3646"></a>コンパイラ エラー C3646

> 'specifier': 不明なオーバーライド指定子

## <a name="remarks"></a>Remarks

オーバーライド指定子では、これが必要ですが、トークンが、コンパイラによって認識されない位置でトークンが見つかりました。

たとえば場合、認識されない*指定子*は **_NOEXCEPT**、キーワードに置き換えます**noexcept**します。

詳細については、次を参照してください。[オーバーライド指定子を](../../extensions/override-specifiers-cpp-component-extensions.md)します。

## <a name="example"></a>例

次の例では、C3646 を生成し、その修正方法を示しています。

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```