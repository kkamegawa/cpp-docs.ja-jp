---
title: コンカレンシー名前空間列挙型 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126954"
---
# <a name="concurrency-namespace-enums-amp"></a>コンカレンシー名前空間列挙型 (AMP)

|||
|-|-|
|[access_type 列挙型](#access_type)|[queuing_mode 列挙型](#queuing_mode)|

## <a name="access_type"></a>access_type 列挙型

データへのさまざまな種類のアクセスを示すために使用される列挙型。

```cpp
enum access_type;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`access_type_auto`|アクセラレータに最も適した `access_type` を自動的に選択します。|
|`access_type_none`|専用。 割り当ては、アクセラレータ上でのみアクセスでき、CPU 上ではアクセスできません。|
|`access_type_read`|共有。 割り当ては、アクセラレータ上でアクセスでき、CPU 上では読み取り可能です。|
|`access_type_read_write`|共有。 割り当ては、アクセラレータ上でアクセスでき、CPU 上では書き込み可能です。|
|`access_type_write`|共有。 割り当ては、アクセラレータ上でアクセスでき、CPU 上では読み取りおよび書き込みの両方ができます。|

## <a name="queuing_mode"></a>queuing_mode 列挙型

アクセラレータでサポートされているキュー モードを指定します。

```cpp
enum queuing_mode;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`queuing_mode_immediate`|[Parallel_for_each 関数 (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)などのすべてのコマンドが、呼び出し元に戻るとすぐに対応するアクセラレータデバイスに送信されることを指定するキューモード。|
|`queuing_mode_automatic`|[Accelerator_view](accelerator-view-class.md)オブジェクトに対応するコマンドキューでコマンドをキューに入れることを指定するキューモード。 コマンドは[accelerator_view:: flush](accelerator-view-class.md#flush)が呼び出されたときにデバイスに送信されます。|

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
