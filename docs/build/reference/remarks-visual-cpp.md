---
title: '&lt;解説 > (C++ドキュメントコメント)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 096280526b12feff33377a705f7c03548a1f0f13
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988648"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

\<remarks> タグを使用して、型の情報を追加し、[\<summary>](summary-visual-cpp.md) で指定された情報を補足します。 この情報は[オブジェクト ブラウザー](/visualstudio/ide/viewing-the-structure-of-code)とコード コメント Web レポートに表示されます。

## <a name="syntax"></a>構文

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>パラメーター

*description*<br/>
メンバーの説明。

## <a name="remarks"></a>Remarks

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>使用例

```cpp
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
