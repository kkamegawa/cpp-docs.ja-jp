---
title: テンプレート ライブラリ (ATL) の使用
ms.date: 11/04/2016
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
ms.openlocfilehash: 7b1a6b0befcfd7ecf0a150653b5c32239b7f9543
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195132"
---
# <a name="using-a-template-library"></a>テンプレート ライブラリの使用

テンプレートは、マクロに似ています。 、マクロを使用して、テンプレートを呼び出すと (適切なパラメーターの置換) の展開を記述したコードにします。 ただし、テンプレート パラメーターとして渡す型に基づいて新しいクラスの作成を許可するようによりもさらに移動します。 これらの新しいクラスは、テンプレート コードで表される操作を実行するタイプ セーフな方法を実装します。

ATL などのテンプレートのライブラリは従来の C++ クラス ライブラリと異なるソース コードとしてのみ (または小さな実行時のサポートでソース コードとして) 通常提供されること、本質的にまたは必ずしも階層構造になっています。 必要な機能を取得するためのクラスから派生するのではなく、テンプレートからのクラスをインスタンス化します。

## <a name="see-also"></a>関連項目

[ATL の概要](../atl/introduction-to-atl.md)
