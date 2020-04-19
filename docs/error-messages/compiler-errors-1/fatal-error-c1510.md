---
title: 致命的なエラー C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 33c17a3099f4aed99cc26579d0e65c4a350b4268
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501092"
---
# <a name="fatal-error-c1510"></a>致命的なエラー C1510

言語リソース clui.dll を開くことができません

コンパイラは言語リソース DLL を読み込めません。

この問題には、2つの一般的な原因があります。 32ビットのコンパイラおよびツールを使用する場合、リンク中に 2 GB を超えるメモリを使用する大規模なプロジェクトでは、このエラーが発生することがあります。 64ビットの Windows システムで考えられる解決策は、64ビットのネイティブまたはクロスコンパイラとツールを使用してコードを生成することです。 これにより、64ビットアプリに使用できる大きなメモリ領域が活用されます。 32ビットシステムで実行されているために32ビットのコンパイラを使用する必要がある場合は、場合によっては、リンカーで使用可能なメモリの量を 3 GB に増やすことができます。 詳細については[、「4 gb のチューニング」を参照してください。Bcdedit と boot.ini](/windows/win32/memory/4-gigabyte-tuning)および[bcdedit/set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set)コマンドを実行します。

その他の一般的な原因は、Visual Studio のインストールが壊れているか不完全であることです。 この場合は、インストーラーを再度実行して、Visual Studio を修復または再インストールします。
