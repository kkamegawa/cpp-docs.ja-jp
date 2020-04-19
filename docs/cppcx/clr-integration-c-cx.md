---
title: CLR 統合 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: 44ef35d1a62706cae37285c06547a8b9b7deb35c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740293"
---
# <a name="clr-integration-ccx"></a>CLR 統合 (C++/CX)

一部の Windows ランタイム型は、/Cx C++および共通言語ランタイム (CLR) に基づく言語で特別な処理を受け取ります。 この記事では、1 つの言語のいくつかの型から別の言語へのマップの仕組みについて説明します。 たとえば、CLR は Windows.Foundation.IVector を System.Collections.IList へ、Windows.Foundation.IMap を System.Collections.IDictionary へ、というようにマップします。 同様にC++、/Cx は platform::D Delegate や platform:: String などの型を特別にマップします。

## <a name="mapping-the-windows-runtime-to-ccx"></a>Windows ランタイムの/Cx へC++のマッピング

/Cx C++が Windows メタデータ (winmd) ファイルを読み取ると、コンパイラは、共通の Windows ランタイム名前空間およびC++型を/cx 名前空間および型に自動的にマップします。 たとえば、数値 Windows ランタイム型`UInt32`はに自動的に`default::uint32`マップされます。

C++/CX は、他のいくつかの Windows ランタイム型を**Platform**名前空間にマップします。 たとえば、読み取り専用の Unicode テキスト文字列を表す**Windows:: Foundation** hstring ハンドルは、 C++/cx `Platform::String`クラスにマップされます。 Windows ランタイム操作からエラー HRESULT が返されると、 C++/cx `Platform::Exception`にマップされます。

またC++、/cx は Windows ランタイム名前空間の特定の型をマップして、型の機能を強化します。 これらの型でC++は、/cx は、にC++固有のヘルパーコンストラクターとメソッドを提供し、型の標準の winmd ファイルでは使用できません。

新しいコンストラクターとヘルパー メソッドをサポートしている値構造体を次の一覧に示します。 構造体の初期化リストを使用するコードを既に作成済みの場合、新たに追加されたコンストラクターを使用するように変更してください。

**Windows::Foundation**

- ポイント

- Rect

- サイズ

**Windows::UI**

- 色

**Windows::UI::Xaml**

- CornerRadius

- 存続期間

- GridLength

- 太さ

**Windows::UI::Xaml::Interop**

- TypeName

**Windows::UI::Xaml::Media**

- [マトリックス]

**Windows::UI::Xaml::Media::Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>CLR を/Cx にC++マップする

Microsoft C++またはC#コンパイラが winmd ファイルを読み取ると、メタデータファイル内の特定の型が適切なC++/cx または CLR 型に自動的にマップされます。 たとえば、CLR では、ivector\<T > インターフェイスは、IList\<t > にマップされます。 ただし、 C++/cx では、ivector\<T > インターフェイスは別の型にマップされません。

Windows ランタイム\<内の IReference t > は、.net\<の null 値を許容する t > にマップされます。

## <a name="see-also"></a>関連項目

[その他の言語との相互運用](../cppcx/interoperating-with-other-languages-c-cx.md)
