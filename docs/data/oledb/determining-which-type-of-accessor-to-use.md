---
title: 使用するアクセサーの種類の決定
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: f32b3375a517c8716324a2d5b35ec16826605f8e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525092"
---
# <a name="determining-which-type-of-accessor-to-use"></a>使用するアクセサーの種類の決定

行セットのデータ型はコンパイル時または実行時に決定することができます。

コンパイル時にデータ型を決定する必要がある場合は、静的アクセサー (`CAccessor` など) を使用します。 

実行時にデータ型を決定する必要がある場合は、動的 (`CDynamicAccessor` またはその子) または手動のアクセサー (`CManualAccessor`) を使用します。 このようなケースでは、行セットに対して `GetColumnInfo` を呼び出して、返された列のバインド情報から型を判断することができます。

コンシューマー テンプレートで提供されるアクセサーの種類を次の表に示します。 どのアクセサーにもメリットとデメリットがあります。 ご自身の状況に応じて、ニーズに合うアクセサーの種類があるはずです。

|アクセサー クラス|バインド|パラメーター|コメント|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|COLUMN_ENTRY マクロを使用してユーザー レコードを作成します。 このマクロは、そのレコード内のデータ メンバーをアクセサーにバインドします。 行セットが作成されると、列のバインドを解除することはできません。|必要 (PARAM_MAP マクロ エントリを使用)。 一度バインドされると、パラメーターのバインドを解除することはできません。|コードが少ないため、最も高速なアクセサーです。|
|`CDynamicAccessor`|自動。|いいえ。|行セット内のデータ型がわからない場合に役立ちます。|
|`CDynamicParameterAccessor`|自動 ([オーバーライド](../../data/oledb/overriding-a-dynamic-accessor.md)可)。|必要 (プロバイダーが `ICommandWithParameters` をサポートしている場合)。 パラメーターは自動的にバインドされます。|`CDynamicAccessor` よりも低速ですが、汎用ストアド プロシージャの呼び出しに便利です。|
|`CDynamicStringAccessor[A,W]`|自動。|いいえ。|文字列データとしてデータ ストアからアクセスされるデータを取得します。|
|`CManualAccessor`|手動 (`AddBindEntry` を使用)。|手動 (`AddParameterEntry` を使用)。|高速。パラメーターと列は 1 回だけバインドされます。 使用するデータ型はユーザーが決定します (例については、[DBVIEWER](https://github.com/Microsoft/VCSamples) サンプルを参照)。`CDynamicAccessor` や `CAccessor` よりも多くのコードが必要です。 OLE DB の直接呼び出しに似ています。|
|`CXMLAccessor`|自動。|いいえ。|文字列データとしてデータ ストアからアクセスされるデータを取得し、それを XML タグ付けデータとして書式設定します。|

## <a name="see-also"></a>関連項目

[アクセサーの使用](../../data/oledb/using-accessors.md)