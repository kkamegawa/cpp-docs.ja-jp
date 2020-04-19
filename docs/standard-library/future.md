---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: c852b3040a94035f6a84b1f717c3583fababbb2c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688026"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

標準ヘッダー \<future > をインクルードして、クラステンプレートや、(場合によっては別のスレッドで) 関数の実行を簡略化し、その結果を取得するためのサポートテンプレートを定義します。 結果は、関数によって返される値、または関数によって生成されるが関数ではキャッチされない例外になります。

このヘッダーではコンカレンシー ランタイム (ConcRT) が使用されます。これにより、このヘッダーを他の ConcRT メカニズムと共に使用できます。 ConcRT の詳細については、「[コンカレンシー ランタイム](../parallel/concrt/concurrency-runtime.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
#include <future>
```

## <a name="remarks"></a>Remarks

> [!NOTE]
> **/Clr**を使用してコンパイルされたコードでは、このヘッダーはブロックされます。

*非同期プロバイダー*は、関数呼び出しの結果を格納します。 関数呼び出しの結果を取得するには、*非同期のリターン オブジェクト*を使用します。 *関連付けられた非同期状態*によって、非同期プロバイダーと 1 つ以上の非同期のリターン オブジェクトの間で通信を実行できます。

プログラムでは、関連付けられた非同期状態のオブジェクトは直接作成されません。 プログラムでは、必要に応じて非同期プロバイダーが作成され、その非同期プロバイダーに基づいて非同期のリターン オブジェクトが作成されます。このリターン オブジェクトでは、その関連付けられた非同期状態がプロバイダーと共有されます。 非同期プロバイダーと非同期のリターン オブジェクトによって、共有済みの関連付けられた非同期状態を保持するオブジェクトが管理されます。 関連付けられた非同期状態を参照する最後のオブジェクトが、その参照を解放すると、関連付けられた非同期状態を保持するオブジェクトが破棄されます。

非同期プロバイダーや、関連付けられた非同期状態を保持しない非同期のリターン オブジェクトは、*空*になります。

関連付けられている非同期状態は、非同期プロバイダーが戻り値を格納した場合か例外を格納した場合のみ*準備完了*になります。

テンプレート関数 `async` およびクラステンプレート `promise` と `packaged_task` は、非同期プロバイダーです。 クラステンプレート `future` および `shared_future`、非同期の戻りオブジェクトを記述します。

各クラステンプレート `promise`、`future`、および `shared_future` には、 **void**型の特殊化と、参照渡しで値を格納および取得するための部分的特殊化があります。 これらの特殊化がプライマリ テンプレートと異なる点は、戻り値を格納および取得する関数のシグネチャとセマンティクスだけです。

クラステンプレート `future` および `shared_future` デストラクターではブロックされません。ただし、旧バージョンとの互換性のために残されている1つのケースは除きます。これは、で開始したタスクにアタッチされる、`future` または最後の `shared_future` の他のすべてのフューチャとは異なり `std::async`では、タスクが完了していない場合、デストラクターはブロックします。つまり、このスレッドが `.get()` または `.wait()` をまだ呼び出しておらず、タスクがまだ実行中である場合は、ブロックされます。 標準の草案では、`std::async` の説明に使用上の注意事項が追加されています。その注意事項とは、「メモ: std::async から取得された future をローカル スコープ外に移動する場合、future を使用する他のコードでは、future のデストラクターは共有状態が準備完了になるのをブロックする可能性があることを考慮する必要があります。」といったものです。ただし、それ以外の場合は、`future` と `shared_future` のデストラクターでは、ブロックが確実に実行されないようにする必要があります。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|名|説明|
|----------|-----------------|
|[future クラス](../standard-library/future-class.md)|非同期のリターン オブジェクトを記述します。|
|[future_error クラス](../standard-library/future-error-class.md)|`future` オブジェクトを管理する型のメソッドによってスローされる例外オブジェクトを記述します。|
|[packaged_task クラス](../standard-library/packaged-task-class.md)|呼び出しラッパーであり、呼び出しシグネチャが `Ty(ArgTypes...)` である非同期プロバイダーを記述します。 その関連付けられた非同期状態には、可能性がある結果に加えて呼び出し可能オブジェクトのコピーが保持されます。|
|[promise クラス](../standard-library/promise-class.md)|非同期プロバイダーを記述します。|
|[shared_future クラス](../standard-library/shared-future-class.md)|非同期のリターン オブジェクトを記述します。 `future` オブジェクトとは異なり、非同期プロバイダーを任意の数の `shared_future` オブジェクトに関連付けることができます。|

### <a name="structures"></a>構造体

|名|説明|
|----------|-----------------|
|[is_error_code_enum 構造体](../standard-library/is-error-code-enum-structure.md)|`future_errc` が `error_code` の格納に適していることを示す特殊化です。|
|[uses_allocator 構造体](../standard-library/uses-allocator-structure.md)|常に true を保持する特殊化です。|

### <a name="functions"></a>関数

|名|説明|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|非同期プロバイダーを表します。|
|[future_category](../standard-library/future-functions.md#future_category)|`error_category` オブジェクトに関連するエラーの特性を設定する `future` オブジェクトへの参照を返します。|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|`error_code` エラーの特性を設定する `error_category` オブジェクトを保持する `future` を作成します。|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|`error_condition` エラーの特性を設定する `error_category` オブジェクトを保持する `future` を作成します。|
|[swap](../standard-library/future-functions.md#swap)|関連付けられた非同期状態を、`promise` オブジェクト間で交換します。|

### <a name="enumerations"></a>列挙

|名|説明|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|`future_error` クラスによって報告されるエラーのシンボル名を提供します。|
|[future_status](../standard-library/future-enums.md#future_status)|期限が設定された wait 関数から返される理由のシンボル名を提供します。|
|[開い](../standard-library/future-enums.md#launch)|テンプレート関数 `async` で使用できるモードを示すビットマスク型を表します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
