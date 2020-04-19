---
title: marshal_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2294d8fe94a32f281332c963b21a542366ae3207
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386084"
---
# <a name="marshalas"></a>marshal_as

このメソッドは、ネイティブ環境とマネージ環境の間でデータを変換します。

## <a name="syntax"></a>構文

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>パラメーター

*input*<br/>
[in]値にマーシャ リングする、`To_Type`変数。

## <a name="return-value"></a>戻り値

`To_Type`の値を変換した後の `input` 型の変数。

## <a name="remarks"></a>コメント

このメソッドは、ネイティブ型とマネージド型の間でデータを変換する簡素化された方法を提供します。 サポートされるデータ型を確認するのを参照してください。 [c++ Overview of Marshaling](../dotnet/overview-of-marshaling-in-cpp.md)します。 一部のデータ変換では、コンテキストが必要です。 使用してこれらのデータ型に変換することができます、 [marshal_context クラス](../dotnet/marshal-context-class.md)します。

サポートされていないデータ型のペアをマーシャ リングしようとする場合`marshal_as`エラーが生成されます[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)コンパイル時にします。 詳細については、このエラーと共に提供されるメッセージを参照してください。 `C4996` エラーは、非推奨の関数の場合に加えて、他の状況で生成される可能性もあります。 このエラーの 1 つの例は、サポートされていない 2 つのデータ型をマーシャリングしようとする場合です。

マーシャリング ライブラリは、複数のヘッダー ファイルで構成されます。 どの変換でもただ 1 つのファイルが必要ですが、他の変換で必要とされる追加ファイルをインクルードすることもできます。 どのファイルにどの変換が関連付けられているかを確認するには、`Marshaling Overview` の表を参照してください。 どの変換を行おうとするかにかかわりなく、名前空間の要件が常に有効になります。

## <a name="example"></a>例

この例では、`const char*` から `System::String` 変数型へのマーシャリングを行います。

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>必要条件

**ヘッダー ファイル:** \<msclr\marshal.h >、 \<msclr\marshal_windows.h >、 \<msclr\marshal_cppstd.h >、または\<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>関連項目

[C++ におけるマーシャリングの概要](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context クラス](../dotnet/marshal-context-class.md)
