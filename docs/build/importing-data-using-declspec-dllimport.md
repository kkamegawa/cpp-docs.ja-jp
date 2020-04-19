---
title: __declspec(dllimport) を使ったデータのインポート
ms.date: 11/04/2016
f1_keywords:
- dllimport
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 74ad93e640a4e961f7670077227bb5c35a42c20f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342107"
---
# <a name="importing-data-using-declspecdllimport"></a>__declspec(dllimport) を使ったデータのインポート

使用して、データの場合は **_declspec**は間接レイヤーの役割を削除する便利な項目です。 DLL からデータをインポートするときにも、インポート アドレス テーブルを通じて行う必要があります。 前に **_declspec**、つまり、DLL からエクスポートされたデータにアクセスするときに、追加のレベルの間接参照を実行する必要があります。

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

内のデータをエクスポートしは、します。DEF ファイル:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

DLL の外部のアクセスします。

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

データとしてマークすると **_declspec**コンパイラは、の間接参照コードを自動的に生成されます。 不要になった、上記の手順について心配する必要があるとします。 既に説明したようには使用しないでください **_declspec** DLL のビルド時にデータを宣言します。 DLL 内の関数では、データ オブジェクトにアクセスするのにインポート アドレス テーブルを使用しないでください。そのため、余分な間接参照が存在するレベルはありません。

DLL から自動的にデータをエクスポートするには、この宣言を使用します。

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>関連項目

[アプリケーションへのインポート](importing-into-an-application.md)
