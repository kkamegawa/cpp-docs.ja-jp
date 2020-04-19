---
title: TemplateInstantiation 化クラス
description: C++ビルドインサイト SDK templateinstantiation 化クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2c94f8d3a4613e072c03f6dd4c846798d3d2122b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334524"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation 化クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TemplateInstantiation` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`TemplateInstantiation` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[TemplateInstantiation インスタンス化](#template-instantiation)

### <a name="functions"></a>関数

[種類](#kind)
[Primarytemplates ymbold キー](#primary-template-symbol-key)
特別[izationシンボルキー](#specialization-symbol-key)

## <a name="kind"></a>同様

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>戻り値

実行されたテンプレートのインスタンス化の種類を記述するコード。

## <a name="primary-template-symbol-key"></a>Primarytemplates Ymbold キー

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>戻り値

特殊化されたテンプレート型の数値識別子。 この識別子は、コンパイラのフロントエンドパス内で一意です。

## <a name="specialization-symbol-key"></a>特別 Izationシンボルキー

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>戻り値

特殊化の型の数値識別子。 この識別子は、コンパイラのフロントエンドパス内で一意です。

## <a name="template-instantiation"></a>TemplateInstantiation インスタンス化

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)イベントです。

::: moniker-end
