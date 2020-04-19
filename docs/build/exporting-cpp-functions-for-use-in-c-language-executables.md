---
title: C 言語の実行形式で使う C++ 関数のエクスポート
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195235"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>C 言語の実行形式で使う C++ 関数のエクスポート

C++ で記述された DLL 内の関数に C 言語のモジュールからアクセスするには、C++ リンケージではなく C リンケージを使って関数を宣言する必要があります。 特に指定しない限り、C++ コンパイラは C++ のタイプ セーフな名前付け規約 (名前の装飾) と C++ の呼び出し規則を使います。C++ の規約を使うと、C からの呼び出しが難しくなります。

C リンケージを指定するには、指定`extern "C"`関数の宣言にします。 例えば:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>実行する操作

- [.Def ファイルを使った DLL からエクスポートします。](exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS を使ったエクスポート/インポート](exporting-and-importing-using-afx-ext-class.md)

- [C または C++ 言語の実行可能ファイルで使用するための C 関数をエクスポートします。](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport) を使用してアプリケーションにインポートする](importing-into-an-application-using-declspec-dllimport.md)

- [DLL を初期化します。](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [装飾名](reference/decorated-names.md)

- [extern を使用したリンケージの指定](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>関連項目

[DLL からのエクスポート](exporting-from-a-dll.md)
