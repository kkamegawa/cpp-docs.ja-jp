---
title: marshal_context クラス
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805982"
---
# <a name="marshalcontext-class"></a>marshal_context クラス

このクラスは、ネイティブおよびマネージ環境間でデータを変換します。

## <a name="syntax"></a>構文

```cpp
class marshal_context
```

## <a name="remarks"></a>Remarks

使用して、`marshal_context`コンテキストを必要とするデータ変換のクラス。 詳細については、どの変換コンテキストが必要し、マーシャ リングするファイルが含まれるが、次を参照してください。 [C++ におけるマーシャ リングの概要](../dotnet/overview-of-marshaling-in-cpp.md)します。 コンテキストを使用する場合にマーシャ リングの結果は有効期限のみ、`marshal_context`オブジェクトは破棄されます。 結果を保持するには、データをコピーする必要があります。

同じ`marshal_context`多数のデータ変換に使用できます。 この方法でコンテキストを再利用すると、マーシャ リングの前の呼び出しの結果は影響しません。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|構築、`marshal_context`マネージとネイティブのデータ型間のデータ変換に使用するオブジェクト。| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|`marshal_context` オブジェクトを破棄します。| 

### <a name="public-methods"></a>パブリック メソッド

|名前|説明| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|マネージとネイティブ データ型の間で変換する特定のデータ オブジェクトにマーシャ リングを実行します。| 


## <a name="requirements"></a>必要条件

**ヘッダー ファイル:** \<msclr\marshal.h >、 \<msclr\marshal_windows.h >、 \<msclr\marshal_cppstd.h >、または\<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

構築、`marshal_context`マネージとネイティブのデータ型間のデータ変換に使用するオブジェクト。

```cpp
marshal_context();
```

### <a name="remarks"></a>Remarks

一部のデータ変換には、マーシャ リング コンテキストが必要です。 翻訳の詳細についてはコンテキストが必要し、アプリケーションに組み込むファイルのどのマーシャ リングする必要がありますを参照してください[C++ におけるマーシャ リングの概要](../dotnet/overview-of-marshaling-in-cpp.md)します。

### <a name="example"></a>例

例をご覧ください[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)します。


## <a name="tilde-marshal-context"></a>marshal_context::~marshal_context

`marshal_context` オブジェクトを破棄します。

```cpp
~marshal_context();
```

### <a name="remarks"></a>Remarks

一部のデータ変換には、マーシャ リング コンテキストが必要です。 参照してください[C++ におけるマーシャ リングの概要](../dotnet/overview-of-marshaling-in-cpp.md)詳細については、コンテキストが必要にどの翻訳とマーシャ リングするファイルは、アプリケーションに含める必要があります。

削除、`marshal_context`オブジェクトがそのコンテキストによって変換されたデータが無効になります。 後にデータを保持する場合、`marshal_context`オブジェクトが破棄された時点で保持される変数にデータを手動でコピーする必要があります。

## <a name="marshal-as"></a>marshal_context::marshal_as

マネージとネイティブ データ型の間で変換する特定のデータ オブジェクトにマーシャ リングを実行します。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>パラメーター

*input*<br/>
[in]値にマーシャ リングする、`To_Type`変数。

### <a name="return-value"></a>戻り値

型の変数`To_Type`の変換後の値である`input`します。

### <a name="remarks"></a>Remarks

この関数は、特定のデータ オブジェクトにマーシャ リングを実行します。 この関数のテーブルで示された変換でのみ使用[C++ におけるマーシャ リングの概要](../dotnet/overview-of-marshaling-in-cpp.md)します。

サポートされておらず、データ型のペアをマーシャ リングしようとする場合`marshal_as`エラーが生成されます[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)コンパイル時にします。 詳細については、このエラーと共に提供されるメッセージを参照してください。 `C4996` エラーは、非推奨の関数の場合に加えて、他の状況で生成される可能性もあります。 このエラーを生成する 2 つの条件はサポートされていないデータ型のペアをマーシャ リングしようとして使用しようと`marshal_as`のコンテキストを必要とする変換。

マーシャリング ライブラリは、複数のヘッダー ファイルで構成されます。 どの変換でもただ 1 つのファイルが必要ですが、他の変換で必要とされる追加ファイルをインクルードすることもできます。 テーブルに`Marshaling Overview in C++`変換ごとに含まれるマーシャ リングするファイルを示します。

### <a name="example"></a>例

この例からのマーシャ リングするためのコンテキストで作成、`System::String`を`const char *`変数の型。 変換後のデータは、コンテキストを削除する行の後に有効になりません。

```cpp
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```