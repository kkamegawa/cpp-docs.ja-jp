---
title: 定義と宣言 (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392246"
---
# <a name="definitions-and-declarations-c"></a>定義と宣言 (C++)

**Microsoft 固有の仕様**

DLL インターフェイスを指すは、システムの一部のプログラムによってエクスポートされる既知のすべての項目 (関数とデータ)つまり、すべての項目として宣言されている**dllimport**または**dllexport**します。 DLL インターフェイスに含まれるすべての宣言は、いずれかを指定する必要があります、 **dllimport**または**dllexport**属性。 ただし、定義をのみ指定する必要があります、 **dllexport**属性。 たとえば、次の関数定義はコンパイラ エラーになります。

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

次のコードでも、エラーが生成します。

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

ただし、次に示す構文は、正しい構文です。

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

使用**dllexport** 、定義を意味、 **dllimport**は宣言を意味します。 使用する必要があります、 **extern**キーワード**dllexport** ; 宣言を強制する定義が含まれる場合は、します。 そのため、次の例は正しいコードになります。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

次の例に、上記の例をさらに明確に示します。

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[dllexport、dllimport](../cpp/dllexport-dllimport.md)