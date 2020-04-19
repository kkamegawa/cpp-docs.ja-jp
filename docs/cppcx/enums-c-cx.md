---
title: 列挙型 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821754"
---
# <a name="enums-ccx"></a>列挙型 (C++/CX)

C++/CX では、標準C++ `scoped  enum`に似た `public enum class` キーワードがサポートされています。 `public enum class` キーワードを使用して宣言された列挙子を使用する場合、列挙体識別子を使用して各列挙子値の範囲を指定する必要があります。

### <a name="remarks"></a>Remarks

`public enum class` など、アクセス指定子を持たない `public`は、標準 C++ の [スコープ列挙体](../cpp/enumerations-cpp.md)として扱われます。

`public enum class` または `public enum struct` の宣言は、任意の整数型の基になる型を持つことができますが、Windows ランタイム自体では、型を int32 にする必要があります。また、フラグの列挙体に対して uint32 を使用することもできます。 次の構文は、 `public enum class` または `public enum struct`の各部分を説明します。

この例は、パブリック列挙型クラスを定義する方法を示しています。

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

この次の例では、それを利用する方法を示しています。

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>使用例

次の例は、列挙型を宣言する方法を示します。

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

次の例は、同等の数値にキャストし、比較を実行する方法を示しています。 列挙子 `One` の使用範囲は `Enum1` 列挙体識別子により指定され、列挙子 `First` の範囲は `Enum2`によって指定されることに注意してください。

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>関連項目

[型システム](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[名前空間参照](../cppcx/namespaces-reference-c-cx.md)
