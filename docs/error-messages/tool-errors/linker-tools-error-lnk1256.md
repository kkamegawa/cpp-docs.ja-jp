---
title: リンカ ツール エラー LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: bedf96262944d59737a39a942021cdec9445f3b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990950"
---
# <a name="linker-tools-error-lnk1256"></a>リンカ ツール エラー LNK1256

ALINK 処理に失敗しました : 理由

LNK1256 の一般的な理由は、アセンブリのバージョン番号が無効であることです。 値 65535 はアセンブリ バージョン番号のいずれの部分にも使用できません。 アセンブリバージョンの有効な範囲は 0-65534 です。

また、指定されたキー コンテナーを ALINK が見つけることができなかった場合は、LNK1256 が発生する場合もあります。 キーコンテナーを削除し、 [sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)を使用して、厳密な名前 CSP にもう一度追加します。

LNK1256 のもう 1 つの理由は、リンカーと Alink.dll の間でのバージョンの不一致です。 このことは、Visual Studio のインストールの破損によって発生する場合があります。 Windows のコントロールパネルの **[プログラムと機能]** を使用して、Visual Studio を修復または再インストールします。

次の例では LNK1256 が生成されます。

```cpp
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```
