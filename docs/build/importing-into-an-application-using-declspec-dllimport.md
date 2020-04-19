---
title: __declspec(dllimport) を使ったアプリケーションへのインポート
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 30e0f6517f2d749962c5cf49dddb1662c9ccf129
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341656"
---
# <a name="import-into-an-application-using-declspecdllimport"></a>__declspec(dllimport) を使ったアプリケーションへのインポート

あるプログラムが DLL によって定義されたパブリック シンボルを使うことを、シンボルをインポートすると言います。 ヘッダー ファイルを作成するときの Dll を使用して、使用すると、ビルドするアプリケーションを使用して、 **_declspec**パブリック シンボルの宣言。 キーワード **_declspec**や .def ファイルをエクスポートするかどうかの動作、**方式**キーワード。

コードを読みやすくするためのマクロを定義 **_declspec**マクロを使用して各インポート シンボルを宣言するとします。

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

使用して **_declspec**は関数の宣言で省略可能ですが、このキーワードを使用する場合、コンパイラがより効率的なコードを生成します。 ただし、使用する必要があります **_declspec**のインポートの実行可能ファイル、DLL のパブリック データ シンボルとオブジェクトにアクセスします。 DLL を使う場合は、引き続きインポート ライブラリとリンクする必要があることに注意してください。

DLL とクライアント アプリケーションには、同じヘッダー ファイルを使うことができます。 こうする場合は、DLL のビルドとクライアント アプリケーションのビルドの区別を示すために、専用のプリプロセッサ シンボルを使います。 例:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>実行する操作

- [DLL を初期化します。](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [インライン関数のインポートとエクスポート](importing-and-exporting-inline-functions.md)

- [相互インポート](mutual-imports.md)

## <a name="see-also"></a>関連項目

[アプリケーションへのインポート](importing-into-an-application.md)
