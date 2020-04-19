---
title: シリアル化 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: 794a71ae9a146b691ba6a4377a7fdf2c3ddd3501
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384674"
---
# <a name="serialization-ccli"></a>シリアル化 (C++/CLI)

シリアル化 (オブジェクトまたはメンバーを永続的なメディアの状態を保存するプロセス) の管理対象のクラス (個々 のフィールドまたはプロパティを含む) でサポートされて、<xref:System.SerializableAttribute>と<xref:System.NonSerializedAttribute>クラス。

## <a name="remarks"></a>Remarks

適用、 **SerializableAttribute**クラス全体をシリアル化またはだけに特定のフィールドやマネージ クラスの部分をシリアル化するプロパティを適用するマネージ クラスのカスタム属性。 使用して、 **NonSerializedAttribute**シリアル化の対象から除外フィールドやマネージ クラスのプロパティにカスタム属性。

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、クラスで`MyClass`(およびプロパティ`m_nCount`) シリアル化可能としてマークされます。 ただし、`m_nData`で示されているプロパティはシリアル化されません、 **NonSerialized**カスタム属性。

### <a name="code"></a>コード

```
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>コメント

"Short name"を使用して、両方の属性を参照できることに注意してください (**Serializable**と**NonSerialized**)。 詳細についてはこの[属性の適用](/dotnet/standard/attributes/applying-attributes)します。

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
