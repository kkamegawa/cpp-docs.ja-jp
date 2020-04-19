---
title: バッファー オーバーフロー
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 7f9864e6b49446ea68d82e76e877ce9c677b893d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410760"
---
# <a name="buffer-overflow"></a>バッファー オーバーフロー

文字のサイズを変更すると、バッファーに文字を配置するときに問題が発生することができます。 次のコードは、文字列から文字をコピー、 `sz`、バッファーに`rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

疑問が浮かびます。最後のバイトが先行バイトをコピーしますか? 次は問題が解決しない、バッファー オーバーフローする可能性がある可能性があるため。

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy`呼び出しが正しいことを行う試行-1 つまたは 2 バイトかどうかは、すべての文字をコピーします。 エントリの文字が 2 バイト幅の場合、コピーする最後の文字が、バッファーが適合しないアカウントにはなりません。 解決するには。

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

このコードは、ループでバッファーのオーバーフローのテストを使用してテスト`_mbclen`によって示される現在の文字のサイズをテストする`sz`します。 呼び出すことによって、`_mbsnbcpy`関数のコードを置き換えることができます、**中**1 行のコードをループします。 例:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>関連項目

[MBCS のプログラミングについて](../text/mbcs-programming-tips.md)
