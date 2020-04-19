---
title: 遅延読み込みされた DLL に対するすべてのインポートの読み込み
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: e855b648dc7a9ee0670c3704a11aa1897a238403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301670"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>遅延読み込みされた DLL に対するすべてのインポートの読み込み

**_ _Hrloadallimportsfordll** delayhlp.cpp で定義されている、関数で指定された DLL からのすべてのインポートを読み込むようにリンカーに指示、 [/delayload](delayload-delay-load-import.md)リンカー オプション。

すべてのインポートの読み込みを使用すると、コード内の 1 つの場所でエラー処理とインポートの実際の呼び出しを処理する例外を使用する必要はありません。 また、インポートの読み込みに失敗したヘルパー コードの結果としてのプロセスをアプリケーションが部分的に失敗する状況を回避できます。

呼び出す **_ _hrloadallimportsfordll**フック関数とエラーの動作は変わりません処理; を参照してください[エラー処理と通知](error-handling-and-notification.md)詳細についてはします。

渡される DLL 名 **_ _hrloadallimportsfordll** DLL 自体の内部に格納されている名前と比較され、大文字と小文字を区別します。

次の例は、呼び出す方法を示しています **_ _hrloadallimportsfordll**:。

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](linker-support-for-delay-loaded-dlls.md)
