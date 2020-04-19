---
title: '&lt;概要 > (C++ドキュメントコメント)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 0620273f24573539897809b7892d46ad49b7aa57
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988576"
---
# <a name="ltsummarygt"></a>&lt;summary&gt;

\<summary> タグは、型または型のメンバーの説明に使用します。 型の説明に補足情報を追加するには、[\<remarks>](remarks-visual-cpp.md) タグを使用します。

## <a name="syntax"></a>構文

```
<summary>description</summary>
```

#### <a name="parameters"></a>パラメーター

*description*<br/>
オブジェクトの概要。

## <a name="remarks"></a>Remarks

\<summary> タグのテキストは、IntelliSense の型に関する唯一のソースで、[オブジェクト ブラウザー](/visualstudio/ide/viewing-the-structure-of-code)とコード コメント Web レポートにも表示されます。

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>使用例

```cpp
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
