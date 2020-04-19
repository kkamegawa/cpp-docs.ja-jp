---
title: 定義と宣言 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 8723c3f09a5e9a8eecf0e552c9f5a7fd9b7f6c68
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152366"
---
# <a name="definitions-and-declarations-c"></a>定義と宣言 (C)

**Microsoft 固有の仕様**

DLL インターフェイスは、システム内のプログラムによってエクスポートされることがわかっているすべての項目 (関数とデータ)、つまり、**dllimport** または `dllexport` として宣言されたすべての項目を参照します。 DLL インターフェイスに含まれるすべての宣言では、**dllimport** か `dllexport` の属性を指定する必要があります。 ただし、定義で指定できるのは `dllexport` 属性のみです。 たとえば、次の関数定義はコンパイラ エラーになります。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

次のコードでも、エラーが生成します。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

ただし、次に示す構文は、正しい構文です。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

`dllexport` の使用は定義を意味し、**dllimport** は宣言を意味します。 宣言を強制するには、`extern` と共に `dllexport` キーワードを使用する必要があります。このようにしない場合、暗黙の定義になります。

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[DLL インポートおよびエクスポート関数](../c-language/dll-import-and-export-functions.md)
