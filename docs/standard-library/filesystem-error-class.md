---
title: filesystem_error クラス
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127202"
---
# <a name="filesystem_error-class"></a>filesystem_error クラス

低レベル システム オーバーフローをレポートするためにスローされるすべての例外のための基底クラス。

## <a name="syntax"></a>構文

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>コメント

このクラスは、\<filesystem> 関数のエラーを報告するためにスローされる例外すべてに対する基底クラスとして機能します。 このメソッドは、型`string`のオブジェクトを格納します。これは、exposition の目的でここで呼び出され`mymesg`ます。 また、とと`path` `mypval2`呼ばれる`mypval1`型の2つのオブジェクトも格納します。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[filesystem_error](#filesystem_error)|メッセージを`filesystem_error`構築します。|

### <a name="functions"></a>関数

|||
|-|-|
|[path1](#path1)|`mypval1` を返します。|
|[path2](#path2)|`mypval2` を返します。|
|[結果](#what)|`NTBS` へのポインターを返します。|

## <a name="requirements"></a>要件

**ヘッダー:** \<ファイルシステム >

**名前空間:** std::experimental::filesystem

## <a name="filesystem_error"></a>filesystem_error

最初のコンストラクターは、 *what_arg*と*ec*からメッセージを構築します。 2番目のコンストラクターは、 *pval1*からメッセージを構築します`mypval1`。このメッセージはに格納されます。 また、3番目のコンストラクターは、 *pval1*からメッセージを構築`mypval1`します`mypval2`。このメッセージは、に格納され、 *pval2*から格納されます。

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>パラメーター

*what_arg*\
指定されたメッセージ。

*c*\
指定されたエラーコードです。

*mypval1*\
さらに指定されたメッセージパラメーター。

*mypval2*\
さらに指定されたメッセージパラメーター。

## <a name="path1"></a>path1

このメンバー関数は、`mypval1` を返します。

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>path2

このメンバー関数は、`mypval2` を返します。

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>結果

このメンバー関数は、( `NTBS` `system_error::what()` `mypval2.native_string()` `runtime_error::what()` `mymesg`可能であれば、、、、 、およびから構成される)へのポインターを返します。`mypval1.native_string()`

```cpp
const char *what() const noexcept;
```
