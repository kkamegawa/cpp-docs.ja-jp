---
title: '&lt;> (C++ドキュメントコメント) を参照してください。'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: 8693646fa37648d1b20c791d99d159f2c81b8ec1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988619"
---
# <a name="ltseegt"></a>&lt;see&gt;

\<see> タグを使用すると、テキスト内でリンクを指定できます。 [\<seealso>](seealso-visual-cpp.md) を使用し、「関連項目」セクションに表示するテキストを指定します。

## <a name="syntax"></a>構文

```
<see cref="member"/>
```

#### <a name="parameters"></a>パラメーター

*member*<br/>
現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。  名前は、一重引用符または二重引用符で囲みます。

コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に解決します。  コンパイラは、`member` が見つからない場合に警告を発行します。

## <a name="remarks"></a>Remarks

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

\<see> の使用例については、[\<summary>](summary-visual-cpp.md) を参照してください。

MSVC コンパイラは、ドキュメントコメント内の1回のパスで cref 参照の解決を試みます。  したがって、C++ のルックアップ規則を使用する場合、コンパイラによってシンボルが見つからないと、参照が未解決としてマークされます。 詳細については、「[\<seealso>](seealso-visual-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次のサンプルでは、コンパイラで参照が解決されるよう、ジェネリック型の cref 参照が作られるしくみを確認できます。

```cpp
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
