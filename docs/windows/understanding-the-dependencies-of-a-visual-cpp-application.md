---
title: Visual C++ アプリケーションの依存関係の理解
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
ms.openlocfilehash: 92db11778de7d31bbab67e649cd58e264da331e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387854"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Visual C++ アプリケーションの依存関係の理解

アプリケーションがどの Visual C++ ライブラリに依存しているかを確認するには、プロジェクトのプロパティを表示します  (ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロパティ]** を選択して、**[プロパティ ページ]** ダイアログ ボックスを開きます)。以前では、Windows 8 では、依存関係のより包括的な画像は、Dependency Walker (depends.exe) も使用できます。 Windows の最新バージョンの[lucasg と依存関係](https://github.com/lucasg/Dependencies)ツールでは、(これは、Microsoft によって保証されないサード パーティのツールです). 同様の機能を提供します。

**[プロパティ ページ]** ダイアログ ボックスで、**[構成プロパティ]** にあるさまざまなページを確認して、依存関係を把握できます。 たとえば、プロジェクトで MFC ライブラリが使用されている状態で、**[構成プロパティ]**、**[全般]** ページで **[MFC の使用]**、**[共有 DLL で MFC を使う]** を選択した場合、実行時のアプリケーションは mfc\<バージョン>.dll などの MFC DLL に依存します。 アプリケーションで MFC が使用されていない状態で、**[構成プロパティ]**、**[C/C++]**、**[コード生成]** ページで **[ランタイム ライブラリ]** の値として **[マルチスレッド デバッグ DLL (/MDd)]** または **[マルチスレッド DLL (/MD)]** を選択した場合、そのアプリケーションは CRT ライブラリに依存する可能性があります。

depends.exe を使用すると、読み込み時にアプリケーションにリンクされた DLL の一覧と、遅延読み込みされた DLL の一覧を確認できます。 実行時に動的に読み込まれた DLL の完全な一覧を取得する必要がある場合は、depends.exe のプロファイル機能を使用して、すべてのコード パスが確実に実行されるまでアプリケーションをテストします。 プロファイル セッションを終了すると、実行時に動的に読み込まれた DLL が表示されます。

depends.exe を使用する場合は、DLL が、他の DLL や特定の DLL バージョンに依存している場合があることに注意してください。 depends.exe は、開発用コンピューターとターゲット コンピューターのどちらでも使用できます。 開発用コンピューターでは、アプリケーションのサポートに必要な DLL を報告します。 ターゲット コンピューターでアプリケーションを実行できない場合は、必要な DLL が見つからないのか、不適切なのかを判断できるように、depends.exe をターゲット コンピューターにコピーして、ツールでアプリケーションを開きます。

アプリケーションが依存する DLL がわかったら、アプリケーションを別のコンピューターに配置するときに共に再頒布する必要がある DLL を判断できます。 ほとんどの場合、システム DLL を再配布する必要はありませんが、Visual C++ ライブラリの DLL の再配布が必要である可能性があります。 詳細については、「[再配布する DLL の決定](determining-which-dlls-to-redistribute.md)」を参照してください。

## <a name="see-also"></a>関連項目

[デスクトップ アプリケーションの配置](deploying-native-desktop-applications-visual-cpp.md)
