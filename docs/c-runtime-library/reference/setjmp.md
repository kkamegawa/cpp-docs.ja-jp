---
title: setjmp
ms.date: 08/14/2018
api_name:
- setjmp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 4a88467f5b94ceae4281a35f1486380a877be2e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948237"
---
# <a name="setjmp"></a>setjmp

プログラムの現在の状態を保存します。

## <a name="syntax"></a>構文

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>パラメーター

*env*<br/>
環境が格納されている変数。

## <a name="return-value"></a>戻り値

スタックの環境を保存した後に 0 を返します。 **Setjmp**が`longjmp`呼び出しの結果としてを返す場合、の `longjmp`値引数を返します。または、の`longjmp` *値*引数が0の場合、 **setjmp**は1を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

**Setjmp**関数は、を使用して`longjmp`、後で復元できるスタック環境を保存します。 **Setjmp**とを一緒に使用`longjmp`して、ローカルでない**goto**を実行する方法を提供します。 これらは一般的に、通常の呼び出し規約や復帰規約を使用せず、前に呼び出されたルーチンのエラー処理または回復コードに実行の制御を渡すために使用されます。

**Setjmp**を呼び出すと、現在のスタック環境が*env*に保存されます。 の後続の呼び出し`longjmp`は、保存された環境を復元し、対応する**setjmp**呼び出しの直後のポイントに制御を戻します。 コントロールを受け取るルーチンにアクセスできるすべての変数 (レジスタ変数を除く) には、`longjmp` が呼び出されたときに保持していた値が含まれます。

**Setjmp**を使用して、ネイティブコードからマネージコードに移動することはできません。

**Microsoft 固有の仕様**

Windows 上C++の Microsoft コードでは、 **longjmp**は例外処理コードと同じスタックアンワインドセマンティクスを使用します。 例外をC++発生させるのと同じ場所で安全に使用できます。 ただし、この使用方法はポータブルではなく、いくつかの重要な注意事項が付属しています。 詳細については、「 [longjmp](longjmp.md)」を参照してください。

**Microsoft 固有の仕様はここまで**

> [!NOTE]
> C++移植可能なコードでは、 `setjmp`オブジェクト`longjmp`のセマンティクスを想定してサポートC++することはできません。 具体的には`setjmp` 、と/ `longjmp` `setjmp`を catch および throw で置き換えると、すべての自動オブジェクトに対して自明ではないデストラクターが呼び出される場合、呼び出しペアの動作は未定義になります。 `longjmp` プログラムC++では、 C++例外処理機構を使用することをお勧めします。

詳細については、「[setjmp/longjmp の使用](../../cpp/using-setjmp-longjmp.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**setjmp**|\<setjmp.h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_fpreset](fpreset.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
