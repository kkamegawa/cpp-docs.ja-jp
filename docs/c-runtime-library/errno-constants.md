---
title: errno 定数
ms.date: 09/17/2018
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
ms.openlocfilehash: 34f92bedfa9606c90196f2e3a5e47dc341b23aea
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898743"
---
# <a name="errno-constants"></a>errno 定数

## <a name="syntax"></a>構文

```
#include <errno.h>
```

## <a name="remarks"></a>Remarks

**errno** 値は、各種エラーが発生したときに [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 変数に割り当てられる定数です。

ERRNO.H には、**errno** 値の定義が含まれています。 ただし、ERRNO.H に指定されているすべての定義が 32 ビット Windows オペレーティング システムで使用されるわけではありません。 ERRNO.H の値の一部は、UNIX 系のオペレーティング システムとの互換性を維持することを目的としています。

32 ビット Windows オペレーティング システムの **errno** 値は、XENIX システムの **errno** 値のサブセットです。 したがって、**errno** 値は、Windows オペレーティング システムのシステム コールが返す実際のエラー コードと必ずしも同じとは限りません。 実際のオペレーティング システムのエラー コードにアクセスするには、この値を含む [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 変数を使用します。

次の **errno** 値がサポートされています。

|定数|説明|
|-|-|
|**ECHILD**|子プロセスが存在しません。|
|**EAGAIN**|これ以上プロセスを生成できません。 これ以上プロセス スロットが足りないか、メモリが不足しているか、または最大の入れ子レベルに達したために、新しいプロセスの生成に失敗しました。|
|**E2BIG**|引数リストが長すぎます。|
|**EACCES**|アクセス許可は拒否されました。 ファイルのアクセス許可の設定では、指定したアクセスは許可されません。 このエラーは、ファイルまたはディレクトリにアクセスしたときのモードが、ファイルまたはディレクトリの属性に合わない場合に発生します。<br/><br/>たとえば、開いていないファイルから読み出そうとしたり、既存の読み取り専用ファイルを書き込みモードで開こうとしたり、ファイルでなくディレクトリを開こうとしたりすると、このエラーが発生します。 MS-DOS オペレーティング システムのバージョン 3.0 以降では、**EACCES** がロック違反または共有違反を示す場合があります。<br/><br/>また、ファイルまたはディレクトリを既存のディレクトリと同じ名前に変更しようとした場合や、既存のディレクトリを削除しようとした場合にも、このエラーが発生します。|
|**EBADF**|ファイル番号が正しくありません。 次の 2 つの原因が考えられます。1) 指定されたファイル記述子が有効な値でないか、開いているファイルを参照していないとき。 2) 読み取り専用モードで開いているファイル、またはデバイスに書き込もうとしたとき。|
|**EDEADLOCK**|リソース デッドロックが発生します。 数値演算関数の引数が、関数の定義域内にありません。|
|**EDOM**|算術演算引数が使用されました。|
|**EEXIST**|ファイルが存在します。 既に存在するファイルを作成しようとしています。 たとえば、 **_O_CREAT** フラグと **_O_EXCL** フラグが **_open** の呼び出しで指定されますが、指定した名前のファイルが既に存在しています。|
|**EILSEQ**|無効なバイト シーケンス (たとえば、MBCS 文字列)。|
|**EINVAL**|無効な引数です。 関数の引数のいずれかに無効な値が指定されています。 たとえば、**fseek** の呼び出しでファイル ポインターの位置決めをするときに、起点として与えられた値がファイルの先頭より前にある場合です。|
|**EMFILE**|開いているファイルが多すぎます。 使用できるファイル記述子が不足しているため、これ以上ファイルを開くことができません。|
|**ENOENT**|該当するファイルまたはディレクトリがありません。 指定したファイルまたはディレクトリは存在しないか、見つかりません。 このメッセージは、指定のファイルが存在しない場合、またはパスのコンポーネントが既存のディレクトリを指定していない場合に発生します。|
|**ENOEXEC**|実行形式エラーです。 実行可能形式でないか、無効な実行可能ファイル形式のファイルを実行しようとしました。|
|**ENOMEM**|コアが不足しています。 メモリ不足のため、目的の操作を実行できません。 たとえば、このメッセージは、子プロセスを実行するためのメモリが不足している場合や、 **_getcwd** の呼び出しで割り当て要求を満たすことができない場合に生成されます。|
|**ENOSPC**|デバイスに空き領域がありません。 デバイスの書き込み可能領域が不足しています (たとえば、ディスクが満杯の場合です)。|
|**ERANGE**|結果が大きすぎます。 数値演算関数の引数が大きすぎて、結果の有効数字の一部またはすべてが失われます。 このエラーは、引数が予想よりも大きい場合に他の関数でも発生することがあります (たとえば、 **_getcwd** の *buffer* の引数が予想より長い場合です)。|
|**EXDEV**|デバイス間リンクがあります。 **rename** 関数を使用して、ファイルを別のデバイスに移動しようとしました。|
|**STRUNCATE**|結果として切り詰められる文字列のコピーまたは連結です。 [_TRUNCATE](../c-runtime-library/truncate.md) をご覧ください。

次の値は、POSIX との互換性のためにサポートされています。 これらは、POSIX 以外のシステムでは必須の値です。

```C
#define E2BIG /* argument list too long */
#define EACCES /* permission denied */
#define EADDRINUSE /* address in use */
#define EADDRNOTAVAIL /* address not available */
#define EAFNOSUPPORT /* address family not supported */
#define EAGAIN /* resource unavailable try again */
#define EALREADY /* connection already in progress */
#define EBADF /* bad file descriptor */
#define EBADMSG /* bad message */
#define EBUSY /* device or resource busy */
#define ECANCELED /* operation canceled */
#define ECHILD /* no child process */
#define ECONNABORTED /* connection aborted */
#define ECONNREFUSED /* connection refused */
#define ECONNRESET /* connection reset */
#define EDEADLK /* resource deadlock would occur */
#define EDESTADDRREQ /* destination address required */
#define EDOM /* argument out of domain */
#define EEXIST /* file exists */
#define EFAULT /* bad address */
#define EFBIG /* file too large */
#define EHOSTUNREACH /* host unreachable */
#define EIDRM /* identifier removed */
#define EILSEQ /* illegal byte sequence */
#define EINPROGRESS /* operation in progress */
#define EINTR /* interrupted */
#define EINVAL /* invalid argument */
#define EIO /* io error */
#define EISCONN /* already connected */
#define EISDIR /* is a directory */
#define ELOOP /* too many synbolic link levels */
#define EMFILE /* too many files open */
#define EMLINK /* too many links */
#define EMSGSIZE /* message size */
#define ENAMETOOLONG /* filename too long */
#define ENETDOWN /* network down */
#define ENETRESET /* network reset */
#define ENETUNREACH /* network unreachable */
#define ENFILE /* too many files open in system */
#define ENOBUFS /* no buffer space */
#define ENODATA /* no message available */
#define ENODEV /* no such device */
#define ENOENT /* no such file or directory */
#define ENOEXEC /* executable format error */
#define ENOLCK /* no lock available */
#define ENOLINK /* no link */
#define ENOMEM /* not enough memory */
#define ENOMSG /* no message */
#define ENOPROTOOPT /* no protocol option */
#define ENOSPC /* no space on device */
#define ENOSR /* no stream resources */
#define ENOSTR /* not a stream */
#define ENOSYS /* function not supported */
#define ENOTCONN /* not connected */
#define ENOTDIR /* not a directory */
#define ENOTEMPTY /* directory not empty */
#define ENOTRECOVERABLE /* state not recoverable */
#define ENOTSOCK /* not a socket */
#define ENOTSUP /* not supported */
#define ENOTTY /* inappropriate io control operation */
#define ENXIO /* no such device or address */
#define EOPNOTSUPP /* operation not supported */
#define EOTHER /* other */
#define EOVERFLOW /* value too large */
#define EOWNERDEAD /* owner dead */
#define EPERM /* operation not permitted */
#define EPIPE /* broken pipe */
#define EPROTO /* protocol error */
#define EPROTONOSUPPORT /* protocol not supported */
#define EPROTOTYPE /* wrong protocol type */
#define ERANGE /* result out of range */
#define EROFS /* read only file system */
#define ESPIPE /* invalid seek */
#define ESRCH /* no such process */
#define ETIME /* stream timeout */
#define ETIMEDOUT /* timed out */
#define ETXTBSY /* text file busy */
#define EWOULDBLOCK /* operation would block */
#define EXDEV /* cross device link */
```

## <a name="see-also"></a>参照

[グローバル定数](../c-runtime-library/global-constants.md)
