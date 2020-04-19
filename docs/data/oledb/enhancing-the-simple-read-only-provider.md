---
title: 単純な読み取り専用プロバイダーの機能の拡張
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: d61f24a9a9abffe836a7f11bd5d1517fddf97fe7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175356"
---
# <a name="enhancing-the-simple-read-only-provider"></a>単純な読み取り専用プロバイダーの機能の拡張

このセクションを拡張する方法を示しています、[単純な読み取り専用プロバイダー](../../data/oledb/implementing-the-simple-read-only-provider.md)前のセクションで作成します。 `IRowsetLocateImpl` 実装が作成、`IRowsetLocate`インターフェイスし、ブックマーク サポートを追加します。

プロバイダーがある場合は、機能を拡張して、トランザクションの処理または行をフェッチするアルゴリズムのパフォーマンスの向上は、プロバイダーの更新を行うしたい場合があります。 ほとんどのプロバイダーの拡張機能には、既存の COM オブジェクトへのインターフェイスの追加が含まれます。

次のトピックの例では、追加することで行フェッチ メカニズムを強化する、`IRowsetLocate`インターフェイス`CAgentRowset`します。 その方法について説明します。

- [RCustomRowset IRowsetLocate から継承する](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)します。

- [コンシューマーに返される列を動的に決定](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)します。

## <a name="see-also"></a>関連項目

[単純な読み取り専用プロバイダーの作成](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
