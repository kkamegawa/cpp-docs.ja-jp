---
title: Windows 上での Linux プログラムの実行
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 6b59d7685aaada3ba44c03da2e5c27c75c8a473a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682385"
---
# <a name="running-linux-programs-on-windows"></a>Windows 上での Linux プログラムの実行

Windows 上で Linux プログラムを実行するには、次のオプションを使用できます。

- Windows Subsystem for Linux (WSL) 上でプログラムをそのまま実行します。 WSL では、ご利用のプログラムは仮想マシンではなく、コンピューターのハードウェア上で直接実行されます。 また、WSL を使用すると、Windows システムと Linux システムとの間でファイル システムを直接呼び出すことができるため、SSL 転送の必要がなくなります。 WSL は、コマンドライン環境として設計されており、グラフィックを多用するアプリケーションにはお勧めできません。 詳細については、「[Linux 用 Windows サブシステムのドキュメント](/windows/wsl/about)」を参照してください。
- プログラムは、ご利用のローカル コンピューターまたは Azure 上の Linux 仮想マシンまたは Docker コンテナーでそのまま実行します。 詳細については、「[Virtual Machines](https://azure.microsoft.com/services/virtual-machines/)」と「[Azure 上の Docker](https://docs.microsoft.com/azure/docker/)」を参照してください。
- [MinGW](http://MinGW.org/) 環境または [MinGW-w64](https://MinGW-w64.org/doku.php) 環境で gcc または clang を使用してプログラムをコンパイルします。この環境には、Linux システム コールから Windows へのシステム コールへの変換レイヤーが用意されています。
- [Cygwin](https://www.cygwin.com/) 環境で gcc または clang を使用してプログラムをコンパイルして実行します。これにより、MinGW または MinGW-w64 と比較してより完全な Linux 環境が Windows 上に実現されます。
- ご利用のコードを Linux から手動で移植し、Microsoft C++ (MSVC) を使用して Windows 用にコンパイルします。 これには、プラットフォームに依存しないコードを個別のライブラリにリファクタリングしてから、Windows 固有のコード (Win32 API や DirectX API など) を使用できるように Linux 固有のコードを再記述する必要があります。 ハイ パフォーマンス グラフィックスを必要とするアプリケーションでは、これが最適なオプションです。

