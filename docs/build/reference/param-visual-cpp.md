---
title: '&lt;param > (ドキュメント コメントの C++)'
ms.date: 11/04/2016
f1_keywords:
- param
- <param>
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
ms.openlocfilehash: d8ea4feddbe1ec2d5898f8ef698cc2d69d255933
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320007"
---
# <a name="ltparamgt"></a>&lt;param&gt;

\<param> タグは、メソッドのいずれか 1 つのパラメーターを説明するためにメソッドの宣言のコメントで使用する必要があります。

## <a name="syntax"></a>構文

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>パラメーター

*name*<br/>
メソッド パラメーターの名前です。  名前は、一重引用符または二重引用符で囲みます。  コンパイラは、`name` が見つからない場合に警告を発行します。

*description*<br/>
パラメーターの説明です。

## <a name="remarks"></a>Remarks

\<param> タグのテキストは、IntelliSense、[オブジェクト ブラウザー](/visualstudio/ide/viewing-the-structure-of-code)、コード コメント Web レポートに表示されます。

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>関連項目

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
