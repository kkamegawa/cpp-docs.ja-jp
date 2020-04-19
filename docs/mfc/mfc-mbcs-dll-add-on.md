---
title: MFC MBCS DLL アドオン
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810372"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL アドオン

MFC とそのマルチバイト文字セット (MBCS) ライブラリのサポートには、Visual Studio を Visual Studio 2013 以降でインストールするときに追加の手順が必要です。

**Visual Studio 2013**: 既定では、Visual Studio 2013 にインストールされている MFC ライブラリは Unicode 開発のみをサポートしています。 **文字セット**プロパティが**マルチバイト文字セットを使用**するように設定されているか**設定さ**れていない Visual Studio 2013 で MFC プロジェクトをビルドするには、MBCS dll が必要です。 [Visual Studio 2013 用のマルチバイト MFC ライブラリ](https://www.microsoft.com/download/details.aspx?id=40770)で DLL をダウンロードします。

**Visual Studio 2015**: UNICODE と MBCS の両方の mfc Dll が visual C++ setup コンポーネントに含まれていますが、mfc のサポートは既定ではインストールされていません。 Visual C++ と MFC は、Visual Studio セットアップではオプションのインストール構成です。 MFC が確実にインストールされるようにするには、セットアップで **［カスタム］** を選択して、 **［プログラミング言語］** で **［Visual C++］** と **［Microsoft Foundation Classes for C++］** が選択されていることを確認します。 既に Visual Studio がインストールされている場合は、MFC プロジェクトを作成しようとしたときに、Visual C++ や MFC のインストールを促すプロンプトが表示されます。

**Visual Studio 2017 以降**: Visual Studio インストーラープログラムの **[オプションコンポーネント]** ペインで **[MFC および ATL サポート]** を選択すると、ワークロード**を使用C++したデスクトップ開発**と共に、Unicode および MBCS MFC dll がインストールされます。 インストールにこれらのコンポーネントが含まれていない場合は、ファイルに移動します。 **[新しいプロジェクト**] ダイアログボックスで、 **[Visual Studio インストーラーを開く]** リンクをクリックします。 詳細については、「 [Visual Studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。

## <a name="see-also"></a>参照

[MFC ライブラリのバージョン](../mfc/mfc-library-versions.md)
