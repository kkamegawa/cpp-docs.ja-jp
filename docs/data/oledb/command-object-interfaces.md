---
title: コマンド オブジェクト インターフェイス
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216370"
---
# <a name="command-object-interfaces"></a>コマンド オブジェクト インターフェイス

コマンド オブジェクトを使用して、`IAccessor`インターフェイス パラメーター バインディングを指定します。 コンシューマーは`IAccessor::CreateAccessor`、配列を渡す`DBBINDING`構造体。 `DBBINDING` 列のバインド (型の長さなど) についてを説明します。 プロバイダーは、構造体を受け取りし、データの転送方法と、変換が必要かどうかを決定します。

`ICommandText`インターフェイスには、テキスト コマンドを指定する方法が用意されています。 `ICommandProperties`インターフェイスは、すべてのコマンド プロパティを処理します。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
