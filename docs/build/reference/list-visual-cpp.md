---
title: '&lt;リスト > (ドキュメント コメントの C++)'
ms.date: 11/04/2016
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: fd5b97ac518bc4075697da7b6ed88ed46bdd8814
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305269"
---
# <a name="ltlistgt"></a>&lt;リスト&gt;

\< > ブロックを使用して、テーブルまたは定義の一覧の見出し行を定義します。 テーブルを定義するときにのみ、見出しの用語のエントリを指定する必要があります。

## <a name="syntax"></a>構文

```
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>パラメーター

*term*<br/>
定義される用語であり、`description` で定義されます。

*description*<br/>
行頭文字または番号付きリストの項目、または `term` の定義です。

## <a name="remarks"></a>Remarks

リスト内の各項目は、\<item> ブロックで指定されます。 定義リストを作成する場合は、`term` と `description` の両方を指定する必要があります。 ただし、テーブル、箇条書きリスト、または番号付きリストの場合は、`description` のエントリを指定するだけで済みます。

リストまたはテーブルでは、必要な数の \<item> ブロックを使用できます。

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>例

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>関連項目

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
