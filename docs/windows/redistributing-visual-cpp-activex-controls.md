---
title: Visual C++ ActiveX コントロールの再配布
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: e8eba02f1a2c5706a91b85e3b20a4e4be557537b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388281"
---
# <a name="redistributing-visual-c-activex-controls"></a>Visual C++ ActiveX コントロールの再配布

Visual C++ 6.0 には、アプリケーションで使用できてその後再配布する ActiveX コントロールが用意されています。 このようなコントロールは Visual C++ には含まれなくなりました。 Visual C++ 6.0 のライセンス契約に基づき、Visual C++ で開発されたアプリケーションでこれらのコントロールを再配布できます。

> [!NOTE]
>  Microsoft では、Visual C++ 6.0 のサポートを終了しています。

再配布可能な Visual C++ 6.0 ActiveX コントロールの一覧については、Visual C++ 6.0 プロダクト CD のディスク 1 に含まれる Common\Redist\Redist.txt を参照してください。

アプリケーションを配布するとき、ActiveX コントロールの .ocx をインストールし、登録する必要があります (Regsvr32.exe を使用)。 また、ターゲット コンピューターに次のシステム ファイルの最新版が含まれている必要があります (アスタリスクはファイルを登録する必要があることを示します)。

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

対象のシステムでこれらの DLL が利用できない場合、該当オペレーティング システムを更新するための所定のメカニズムを利用して更新する必要があります。 Windows オペレーティング システムの最新サービス パックは [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com) からダウンロードできます。

データベースに接続する ActiveX コントロールを使用するとき、ターゲット コンピューターでデータ ソース名を複製する必要もあります。 複製は、`ConfigDSN` などの関数を使用してプログラムで行うことができます。

一部の再配布可能 ActiveX コントロールでは、依存関係がさらに増えます。 Visual C++ 6.0 プロダクト CD の OS\システム フォルダーにある .ocx ファイルごとに .dep ファイルもあります。 再配布する .ocx ファイルごとに、それに対応する .dep ファイルで 1 つまたは複数の USES エントリを探してください。 ファイルが一覧表示されている場合、ファイルがターゲット コンピューターにあることを確認する必要があります。 .ocx ファイルを直接サポートする DLL はすべて登録する必要があります。 (Regsvr32.exe を正常に実行するには、コントロールによって静的に読み込まれるすべての DLL がターゲット コンピューターに含まれている必要があります。)さらに、依存関係として一覧表示されている DLL に Visual C++ 6.0 CD の OS/システム フォルダーの .dep ファイルも含まれている場合、その .dep ファイルでも USES エントリを探す必要があります。

## <a name="see-also"></a>関連項目

[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)
