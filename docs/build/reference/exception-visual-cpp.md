---
title: '&lt;例外 > (C++ドキュメントコメント)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: ddfe647fa2db55b3ca606265011896a66398a8a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988295"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

\<exception> タグを使用すると、スローできる例外を指定できます。 このタグは、メソッドの定義に適用されます。

## <a name="syntax"></a>構文

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>パラメーター

*member*<br/>
現在のコンパイル環境から使用できる例外の参照。 名前参照ルールを使用し、コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。  コンパイラは、`member` が見つからない場合に警告を発行します。

名前は、一重引用符または二重引用符で囲みます。

ジェネリック型への cref 参照を作成する方法については、[\<see>](see-visual-cpp.md) を参照してください。

*description*<br/>
説明です。

## <a name="remarks"></a>Remarks

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

MSVC コンパイラは、ドキュメントコメント内の1回のパスで cref 参照の解決を試みます。  したがって、C++ のルックアップ規則を使用する場合、コンパイラによってシンボルが見つからないと、参照が未解決としてマークされます。 詳細については、「[\<seealso>](seealso-visual-cpp.md)」を参照してください。

## <a name="example"></a>使用例

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
