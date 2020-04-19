---
title: '方法: 内部ポインターとマネージド配列を宣言して使用す(C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
ms.openlocfilehash: 0f7ec6551b09b2125fdb21736a851dae0dadbd4a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516337"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>方法: 内部ポインターとマネージド配列を宣言して使用す(C++/CLI)

次の C++/CLI の例では、配列への内部ポインターを宣言して使用する方法を示します。

> [!IMPORTANT]
> この言語機能は、`/clr` コンパイラ オプションではサポートされていますが、`/ZW` コンパイラ オプションではサポートされていません。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>関連項目

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)