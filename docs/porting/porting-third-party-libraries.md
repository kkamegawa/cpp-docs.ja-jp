---
title: サードパーティ ライブラリの移植
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627193"
---
# <a name="porting-third-party-libraries"></a>サード パーティ ライブラリの移植

プロジェクトを Visual Studio 2013 以前のバージョンから現在のバージョンの Visual C++にアップグレードする場合は、ライブラリとプロジェクトが同じバージョンとフレーバーでビルドされるように、プロジェクトが使用するすべてのライブラリをアップグレードする必要もあります。 ライブラリのソースコードにアクセスできず、そのライブラリが vcpkg で使用できない場合は、ライブラリのベンダから更新されたバイナリを取得する必要があります。 詳細については、「[アップグレード時の潜在的な問題の概要](overview-of-potential-upgrade-issues-visual-cpp.md)」 を参照してください。

アプリケーションを Visual Studio 2015 または Visual Studio 2017 から Visual Studio 2019 にアップグレードする場合、依存関係をアップグレードする必要はありません。これは、3つのバージョンで生成されるコードがバイナリ互換であるためです。 詳細については、「 [ C++ visual studio 2015 と visual studio 2019 間のバイナリの互換性](binary-compat-2015-2017.md)」を参照してください。

## <a name="vcpkg-for-open-source-libraries"></a>オープンソースライブラリの vcpkg

これまでは、サードパーティ ライブラリの検索とアップグレードが困難な作業となる場合がありました。 サードパーティのオープンソースライブラリの取得C++と再構築を簡単にするためにC++ 、ビジュアルチームは**VC + + パッケージ化ツール**または**vcpkg**と呼ばれるコマンドラインツールを作成しました。 vcpkg には、多くの一般的な C++ オープンソース ライブラリの、検索可能なカタログがあります。 vcpkg コマンドラインから、カタログ内の任意のライブラリを直接インストールすることができます。 ライブラリをインストールすると、vcpkg によってコンピューターにディレクトリ ツリーが作成され、このフォルダー内に .h、.lib、およびバイナリが追加されます。 このフォルダーは、コンパイル コマンドラインで使用することも、vcpkg integrate install コマンドによって Visual Studio 2015 以降に統合することもできます。 ライブラリの場所を統合すると、Visual Studio でそのライブラリの場所を検索したり、作成した新しいプロジェクトに追加したりすることができます。 ライブラリを使用するには、それを `#include` するだけです。あとは、Visual Studio が自動的にプロジェクト設定への .lib パスを追加し、ソリューション フォルダーに dll をコピーします。 詳細については、「[vcpkg: C++ 用のパッケージ マネージャー](../build/vcpkg.md)」を参照してください。

## <a name="reporting-issues"></a>レポートの問題

オープンソースライブラリが**vcpkg**カタログに存在しない場合は、 [GitHub リポジトリ](https://github.com/Microsoft/vcpkg/issues)で問題を開くことができます。そこで、コミュニティC++とビジュアルチームがこのライブラリを参照して、このライブラリのポートファイルを作成する可能性があります。

## <a name="see-also"></a>関連項目

[Visual C++ 移植とアップグレードのガイド](visual-cpp-porting-and-upgrading-guide.md)
