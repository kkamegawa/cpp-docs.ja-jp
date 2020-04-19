---
title: EventGroup クラス
description: C++ビルドインサイト SDK eventgroup クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ac8ac70f3fc160714b86dd0c483808a4d06e7699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334920"
---
# <a name="eventgroup-class"></a>EventGroup クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`EventGroup` クラステンプレートは、すべてのグループキャプチャクラスの基本クラスです。

## <a name="syntax"></a>構文

```cpp
template <typename TActivity>
class EventGroup;
{
public:
    size_t Size() const;

    const TActivity& operator[](size_t index) const;
    const TActivity& Front() const;
    const TActivity& Back() const;

    std::deque<TActivity>::const_iterator begin() const;
    std::deque<TActivity>::const_iterator end() const;
};
```

### <a name="parameters"></a>パラメーター

*Tactivity*グループに含まれるアクティビティの種類。

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

[バック](#back)
[begin](#begin)
[end](#end)
[Front](#front)
[operator []](#subscript-operator)
[Size](#size)

## <a name="back"></a>戻る

```cpp
const TActivity& Back() const;
```

### <a name="return-value"></a>戻り値

グループ内の最後のアクティビティイベントへの参照。

## <a name="begin"></a>初め

```cpp
std::deque<TActivity>::const_iterator begin() const;
```

### <a name="return-value"></a>戻り値

アクティビティイベントグループの先頭を指す反復子。

## <a name="end"></a>終わり

```cpp
std::deque<TActivity>::const_iterator end() const;
```

### <a name="return-value"></a>戻り値

アクティビティイベントグループの末尾の1つ後ろの位置を指す反復子。

## <a name="front"></a>外側

```cpp
const TActivity& Front() const;
```

### <a name="return-value"></a>戻り値

グループ内の最初のアクティビティイベントへの参照。

## <a name="subscript-operator"></a>演算子 []

```cpp
const TActivity& operator[](size_t index) const;
```

### <a name="parameters"></a>パラメーター

*インデックス*\
アクティビティイベントグループ内のアクセスする要素のインデックス。

### <a name="return-value"></a>戻り値

*インデックス*によって示される位置に格納されているイベントスタックからのイベント。

## <a name="size"></a>幅

```cpp
size_t Size() const;
```

### <a name="return-value"></a>戻り値

イベントグループのサイズ。

::: moniker-end
