---
title: '方法: マーシャ リング ライブラリを拡張します。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: f289539807b1e9499cef51427d3f6a494545cc60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387306"
---
# <a name="how-to-extend-the-marshaling-library"></a>方法: マーシャ リング ライブラリを拡張します。

このトピックでは、データ型の間での複数の変換を提供するマーシャ リング ライブラリを拡張する方法について説明します。 ユーザーは、データ変換を実行するライブラリによってサポートされていないマーシャ リング ライブラリを拡張できます。

有無にかかわらず 2 つの方法のいずれかでマーシャ リング ライブラリを拡張することができます、 [marshal_context クラス](../dotnet/marshal-context-class.md)します。 レビュー、 [c++ Overview of Marshaling](../dotnet/overview-of-marshaling-in-cpp.md)コンテキストを新しい変換が必要かどうかを確認するにはトピック。

どちらの場合では、まず新しいマーシャ リング変換のファイルを作成します。 標準のマーシャ リング ライブラリ ファイルの整合性を保持するための操作を行います。 プロジェクトを別のコンピューターまたは別のプログラマに移植する場合は、プロジェクトの残りの部分と共に新しいマーシャ リング ファイルをコピーする必要があります。 この方法でプロジェクトを受信するユーザーは新しい変換を受信する保証し、すべてのライブラリ ファイルを変更する必要はありません。

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>コンテキストが不要な変換でマーシャ リング ライブラリを拡張するには

1. 新しいマーシャ リング関数 MyMarshal.h などを格納するファイルを作成します。

1. マーシャ リング ライブラリ ファイルの 1 つ以上を含めます。

   - 基本型 marshal.h します。

   - windows のデータ型の marshal_windows.h します。

   - marshal_cppstd.hC++標準ライブラリのデータ型。

   - ATL のデータ型の marshal_atl.h します。

1. 次の手順の最後に、コードを使用すると、変換関数を記述できます。 このコードでは、型に変換する、FROM は、変換後の型と`from`変換されるパラメーターです。

1. 変換ロジックに関するコメントを変換するコードに置き換えます、 `from` TO のオブジェクトにパラメーターを入力し、変換されたオブジェクトを返します。

```
namespace msclr {
   namespace interop {
      template<>
      inline TO marshal_as<TO, FROM> (const FROM& from) {
         // Insert conversion logic here, and return a TO parameter.
      }
   }
}
```

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>コンテキストが必要な変換でマーシャ リング ライブラリを拡張するには

1. 新しいマーシャ リング関数 MyMarshal.h などを格納するファイルを作成します。

1. マーシャ リング ライブラリ ファイルの 1 つ以上を含めます。

   - 基本型 marshal.h します。

   - windows のデータ型の marshal_windows.h します。

   - marshal_cppstd.hC++標準ライブラリのデータ型。

   - ATL のデータ型の marshal_atl.h します。

1. 次の手順の最後に、コードを使用すると、変換関数を記述できます。 このコードでは、型に変換する、FROM から、変換後の型は、 `toObject` 、結果を格納するためのポインターと`fromObject`変換されるパラメーターです。

1. コメントを初期化するコードを初期化する方法について、`toPtr`を適切な空の値。 たとえば、ポインターである場合に設定`NULL`します。

1. 変換ロジックに関するコメントを変換するコードに置き換えます、`from`パラメーターのオブジェクトに*TO*型。 この変換されたオブジェクトに格納されます`toPtr`します。

1. 設定に関するコメント`toObject`を設定するコードで`toObject`変換されたオブジェクトにします。

1. によって割り当てられたメモリを解放するコードとネイティブ リソースのクリーンアップに関するコメントを`toPtr`します。 場合`toPtr`を使用してメモリを割り当てられた`new`を使用して、`delete`メモリを解放します。

```
namespace msclr {
   namespace interop {
      template<>
      ref class context_node<TO, FROM> : public context_node_base
      {
      private:
         TO toPtr;
      public:
         context_node(TO& toObject, FROM fromObject)
         {
            // (Step 4) Initialize toPtr to the appropriate empty value.
            // (Step 5) Insert conversion logic here.
            // (Step 6) Set toObject to the converted parameter.
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // (Step 7) Clean up native resources.
         }
      };
   }
}
```

## <a name="example"></a>例

次の例では、コンテキストが不要な変換でマーシャ リング ライブラリを拡張します。 この例では、コードは、ネイティブ データ型のマネージ データ型に従業員情報を変換します。

```
// MyMarshalNoContext.cpp
// compile with: /clr
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   char* name;
   char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {
         ManagedEmp^ toValue = gcnew ManagedEmp;
         toValue->name = marshal_as<System::String^>(from.name);
         toValue->address = marshal_as<System::String^>(from.address);
         toValue->zipCode = from.zipCode;
         return toValue;
      }
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   NativeEmp employee;

   employee.name = "Jeff Smith";
   employee.address = "123 Main Street";
   employee.zipCode = 98111;

   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);

   Console::WriteLine("Managed name: {0}", result->name);
   Console::WriteLine("Managed address: {0}", result->address);
   Console::WriteLine("Managed zip code: {0}", result->zipCode);

   return 0;
}
```

前の例では、`marshal_as`関数は、変換後のデータにハンドルを返します。 これは、データの追加のコピーが作成されないようにするために行われました。 変数を直接返すことが、不要なパフォーマンス コストに関連付けられていること。

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>例

次の例は、従業員情報をマネージ データ型からネイティブ データ型に変換します。 この変換では、マーシャ リング コンテキストが必要です。

```
// MyMarshalContext.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   const char* name;
   const char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base
      {
      private:
         NativeEmp* toPtr;
         marshal_context context;
      public:
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)
         {
            // Conversion logic starts here
            toPtr = NULL;

            const char* nativeName;
            const char* nativeAddress;

            // Convert the name from String^ to const char*.
            System::String^ tempValue = fromObject->name;
            nativeName = context.marshal_as<const char*>(tempValue);

            // Convert the address from String^ to const char*.
            tempValue = fromObject->address;
            nativeAddress = context.marshal_as<const char*>(tempValue);

            toPtr = new NativeEmp();
            toPtr->name = nativeName;
            toPtr->address = nativeAddress;
            toPtr->zipCode = fromObject->zipCode;

            toObject = toPtr;
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // When the context is deleted, it will free the memory
            // allocated for toPtr->name and toPtr->address, so toPtr
            // is the only memory that needs to be freed.
            if (toPtr != NULL) {
               delete toPtr;
               toPtr = NULL;
            }
         }
      };
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   ManagedEmp^ employee = gcnew ManagedEmp();

   employee->name = gcnew String("Jeff Smith");
   employee->address = gcnew String("123 Main Street");
   employee->zipCode = 98111;

   marshal_context context;
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);

   if (result != NULL) {
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",
         result->name, result->address, result->zipCode);
   }

   return 0;
}
```

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>関連項目

[C++ におけるマーシャリングの概要](../dotnet/overview-of-marshaling-in-cpp.md)
