---
title: '方法: WRL コンポーネントを直接インスタンス化します。'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: 3caa29125de0de8cbe73379b8d7244206a5f9229
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336827"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>方法: WRL コンポーネントを直接インスタンス化します。

Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用する方法について説明します[Microsoft::WRL::Make](make-function.md)と[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)関数モジュールからコンポーネントをインスタンス化します。これを定義します。

コンポーネントを直接インスタンス化することにより、クラス ファクトリやその他の機構が必要ない場合にオーバーヘッドを低減できます。 両方のユニバーサル Windows プラットフォーム アプリおよびデスクトップ アプリで直接のコンポーネントをインスタンス化することができます。

Windows ランタイム C++ テンプレート ライブラリを使用して、従来の COM コンポーネントを作成し、外部のデスクトップ アプリからインスタンスを作成する方法については、次を参照してください。[方法。従来の COM コンポーネントを作成する](how-to-create-a-classic-com-component-using-wrl.md)します。

このドキュメントでは、2 つの例を示します。 最初の例では、`Make` 関数を使用してコンポーネントをインスタンス化します。 2 番目の例では、`MakeAndInitialize` 関数を使用して構築中に失敗する場合があるコンポーネントをインスタンス化します  (通常、COM は、例外の代わりに、HRESULT 値を使用するため、エラーを示す COM 型通常はスローされません、コンス トラクター。 `MakeAndInitialize` を使用すると、コンポーネントで `RuntimeClassInitialize` メソッドを使用して構築引数を検証できます)。どちらの例も、基本的なロガー インターフェイスを定義し、コンソールにメッセージを記述するクラスを定義することでそのインターフェイスを実装します。

> [!IMPORTANT]
> 使用することはできません、 `new` Windows ランタイム C++ テンプレート ライブラリのコンポーネントをインスタンス化する演算子。 そのため、コンポーネントを直接インスタンス化するには、常に `Make` または `MakeAndInitialize` を使用することをお勧めします。

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>基本的なロガー コンポーネントを作成してインスタンス化するには

1. Visual Studio で、作成、 **Win32 コンソール アプリケーション**プロジェクト。 など、プロジェクトの名前*WRLLogger*します。

2. 追加、 **Midl ファイル (.idl)** をプロジェクトにファイルをファイルに名前を`ILogger.idl`、このコードを追加。

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. 次のコードを使用して、内容を置き換える`WRLLogger.cpp`します。

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>基本的なロガー コンポーネントの構造エラーを処理するには

1. 次のコードを使用して `CConsoleWriter` クラスの定義を置き換えます。 このバージョンは、プライベート文字列のメンバー変数を保持し、`RuntimeClass::RuntimeClassInitialize` メソッドをオーバーライドします。 `RuntimeClassInitialize` は `SHStrDup` の呼び出しに失敗すると失敗します。

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. 次のコードを使用して `wmain` の定義を置き換えます。 このバージョンでは`MakeAndInitialize`をインスタンス化する、`CConsoleWriter`オブジェクトし、HRESULT の結果を確認します。

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::WRL::Make](make-function.md)<br/>
[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)