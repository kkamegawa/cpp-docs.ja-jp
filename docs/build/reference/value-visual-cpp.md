---
title: '&lt;値 > (C++ドキュメントコメント)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: de84d1faca59a6c8e4f82fba3605cbd54a05bd2e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988596"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

\<value> タグでは、プロパティとプロパティ アクセサー メソッドを記述することができます。 Visual Studio 統合開発環境では、コード ウィザードを使用してプロパティを追加するときに、新しいプロパティの [\<summary>](summary-visual-cpp.md) タグが追加されることに注意してください。 その後、手動で \<value> タグを追加してプロパティが表す値を記述する必要があります。

## <a name="syntax"></a>構文

```
<value>property-description</value>
```

#### <a name="parameters"></a>パラメーター

*property-description*<br/>
プロパティの説明。

## <a name="remarks"></a>Remarks

コンパイル時に [/doc](doc-process-documentation-comments-c-cpp.md) を指定して、ドキュメント コメントをファイルに出力します。

## <a name="example"></a>使用例

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>参照

[XML に関するドキュメント](xml-documentation-visual-cpp.md)
