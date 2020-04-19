---
title: 型の転送 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: c5148c05e5580942d885b310e35f3b629224a654
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515977"
---
# <a name="type-forwarding-ccli"></a>型の転送 (C++/CLI)

*型を転送する*ことで、アセンブリ A を使用するクライアントの再コンパイルなしで、アセンブリ (アセンブリ A) の型を別のアセンブリ (アセンブリ B) に移動できます。

## <a name="windows-runtime"></a>Windows ランタイム

Windows ランタイムでは、この機能はサポートされていません。

## <a name="common-language-runtime"></a>共通言語ランタイム

次のコード例では、型の転送の使用方法を示します。

### <a name="syntax"></a>構文

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>パラメーター

*new*<br/>
型定義の移動先となるアセンブリ。

*type*<br/>
別のアセンブリに定義を移動する型。

### <a name="remarks"></a>解説

コンポーネント (アセンブリ) が公開され、クライアント アプリケーションによって使用された後、型の転送を使用してコンポーネント (アセンブリ) から別のアセンブリに型を移動し、更新されたコンポーネント (必要に応じて追加されたアセンブリ) を公開できます。コンポーネントは、クライアント アプリケーションの再コンパイルなしで機能します。

型の転送は、既存のアプリケーションによって参照されるコンポーネントに対してのみ機能します。 アプリケーションのリビルドでは、アプリケーションで使用されている型の適切なアセンブリ参照が必要です。

アセンブリから型 (型 A) を転送するときは、アセンブリ参照の他に、その型の `TypeForwardedTo` 属性を追加する必要があります。 参照されるアセンブリには、次のいずれかを含める必要があります。

- 型 A の定義。

- アセンブリ参照と型 A の `TypeForwardedTo` 属性。

転送可能な型の例は次のとおりです。

- ref クラス

- 値クラス

- 列挙型

- インターフェイス

次の型は転送できません。

- ジェネリック型

- ネイティブ型

- 入れ子にされた型 (入れ子にされた型を転送する場合は、それを囲む型を転送する必要があります)

共通言語ランタイムをターゲットとする任意の言語で作成されたアセンブリに型を転送できます。

そのため、アセンブリ A.dll をビルドするために使用されるソース コード ファイルに型定義 (`ref class MyClass`) が含まれているときに、その型定義をアセンブリ B.dll に移動する場合は、以下を実行します。

1. `MyClass` 型定義を、B.dll をビルドするために使用されるソース コード ファイルに 移動します。

2. アセンブリ B.dll をビルドします。

3. A.dll をビルドするために使用されるソース コードから `MyClass` 型定義を削除し、それを以下に置き換えます。

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. アセンブリ A.dll をビルドします。

5. クライアント アプリケーションの再コンパイルなしで、A.dll を使用します。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`