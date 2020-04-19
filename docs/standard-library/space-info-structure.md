---
title: space_info 構造体
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: 2a9856746a8bbc796871663a81bd8911d34dcd4a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457557"
---
# <a name="spaceinfo-structure"></a>space_info 構造体

ボリュームに関する情報を保持します。

## <a name="syntax"></a>構文

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|`unsigned long long capacity`|ボリュームを表すことのできるバイト数の合計数を表します。|
|`unsigned long long free`|ボリューム上のデータを表すために使用されないバイト数を表します。|
|`unsigned long long available`|ボリューム上のデータを表すために使用できるバイト数を表します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ファイルシステム >

**名前空間:** std::experimental::filesystem

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[ファイル システムのナビゲーション (C++)](../standard-library/file-system-navigation.md)
