---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 7dbe4381465036bdd102b3be753a18451886a3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166257"
---
# <a name="typename"></a>typename

テンプレートの定義で、不明な識別子が型であるコンパイラに対するヒントを提供します。 テンプレート パラメーター リストでは、型パラメーターを指定に使用されます。

## <a name="syntax"></a>構文

```
typename identifier;
```

## <a name="remarks"></a>Remarks

テンプレート定義内の名前がテンプレート引数に依存する修飾名である場合、このキーワードを使用する必要があります。修飾名に依存しない場合は省略可能です。 詳細については、次を参照してください。[テンプレートと名前解決](../cpp/templates-and-name-resolution.md)します。

**typename**任意の型定義またはテンプレート宣言の任意の場所で使用できます。 テンプレート基底クラスへのテンプレート引数として使用する場合を除いて、このキーワードを基底クラス リストで使用することはできません。

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**typename**の代わりにキーワードを使用することも**class**テンプレート パラメーターの一覧表示されます。 たとえば、次のステートメントと同じ意味です。

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>例

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>関連項目

[テンプレート](../cpp/templates-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)