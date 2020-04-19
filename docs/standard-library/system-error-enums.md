---
title: '&lt;system_error&gt; 列挙型'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::errc
- system_error/std::io_errc
ms.assetid: b21321b7-404a-40de-8777-a85b77c6fa58
ms.openlocfilehash: cff8a58545409c4358cd303e41d27520edd5d552
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257781"
---
# <a name="ltsystem_errorgt-enums"></a>&lt;system_error&gt; 列挙型

## <a name="errc"></a>errc

`<errno.h>`の POSIX で定義されているすべてのエラーコードマクロにシンボル名を提供します。

```cpp
class errc {
   address_family_not_supported = EAFNOSUPPORT,
   address_in_use = EADDRINUSE,
   address_not_available = EADDRNOTAVAIL,
   already_connected = EISCONN,
   argument_list_too_long = E2BIG,
   argument_out_of_domain = EDOM,
   bad_address = EFAULT,
   bad_file_descriptor = EBADF,
   bad_message = EBADMSG,
   broken_pipe = EPIPE,
   connection_aborted = ECONNABORTED,
   connection_already_in_progress = EALREADY,
   connection_refused = ECONNREFUSED,
   connection_reset = ECONNRESET,
   cross_device_link = EXDEV,
   destination_address_required = EDESTADDRREQ,
   device_or_resource_busy = EBUSY,
   directory_not_empty = ENOTEMPTY,
   executable_format_error = ENOEXEC,
   file_exists = EEXIST,
   file_too_large = EFBIG,
   filename_too_long = ENAMETOOLONG,
   function_not_supported = ENOSYS,
   host_unreachable = EHOSTUNREACH,
   identifier_removed = EIDRM,
   illegal_byte_sequence = EILSEQ,
   inappropriate_io_control_operation = ENOTTY,
   interrupted = EINTR,
   invalid_argument = EINVAL,
   invalid_seek = ESPIPE,
   io_error = EIO,
   is_a_directory = EISDIR,
   message_size = EMSGSIZE,
   network_down = ENETDOWN,
   network_reset = ENETRESET,
   network_unreachable = ENETUNREACH,
   no_buffer_space = ENOBUFS,
   no_child_process = ECHILD,
   no_link = ENOLINK,
   no_lock_available = ENOLCK,
   no_message_available = ENODATA,
   no_message = ENOMSG,
   no_protocol_option = ENOPROTOOPT,
   no_space_on_device = ENOSPC,
   no_stream_resources = ENOSR,
   no_such_device_or_address = ENXIO,
   no_such_device = ENODEV,
   no_such_file_or_directory = ENOENT,
   no_such_process = ESRCH,
   not_a_directory = ENOTDIR,
   not_a_socket = ENOTSOCK,
   not_a_stream = ENOSTR,
   not_connected = ENOTCONN,
   not_enough_memory = ENOMEM,
   not_supported = ENOTSUP,
   operation_canceled = ECANCELED,
   operation_in_progress = EINPROGRESS,
   operation_not_permitted = EPERM,
   operation_not_supported = EOPNOTSUPP,
   operation_would_block = EWOULDBLOCK,
   owner_dead = EOWNERDEAD,
   permission_denied = EACCES,
   protocol_error = EPROTO,
   protocol_not_supported = EPROTONOSUPPORT,
   read_only_file_system = EROFS,
   resource_deadlock_would_occur = EDEADLK,
   resource_unavailable_try_again = EAGAIN,
   result_out_of_range = ERANGE,
   state_not_recoverable = ENOTRECOVERABLE,
   stream_timeout = ETIME,
   text_file_busy = ETXTBSY,
   timed_out = ETIMEDOUT,
   too_many_files_open_in_system = ENFILE,
   too_many_files_open = EMFILE,
   too_many_links = EMLINK,
   too_many_synbolic_link_levels = ELOOP,
   value_too_large = EOVERFLOW,
   wrong_protocol_type = EPROTOTYPE,
};
```

### <a name="remarks"></a>コメント

## <a name="io_errc"></a>io_errc

\<iostream> にエラー状態のシンボル名を提供します。 [ios_base::failure](../standard-library/error-condition-class.md)[ 関数によって返される値と比較される ](../standard-library/ios-base-class.md#failure)error_condition`code()` オブジェクトを作成するために使用できます。

```cpp
class io_errc {
   stream = 1
};
```

### <a name="remarks"></a>コメント

[std::make_error_code()](../standard-library/system-error-functions.md#make_error_code) と [std::make_error_condition()](../standard-library/system-error-functions.md#make_error_condition) の両方が、この列挙型に対してオーバーロードされます。

`ios_base::failure` は、`error_condition` 以外のエラー コードのカテゴリを含むことができます。

### <a name="example"></a>例

```cpp
// io_errc.cpp
// cl.exe /nologo /W4 /EHsc /MTd

#include <iostream>

using namespace std;

int main()
{
    cin.exceptions(ios::failbit | ios::badbit);

    try {
        cin.rdbuf(nullptr); // throws io_errc::stream
    }
    catch (ios::failure& e) {
        cerr << "ios failure caught: ";
        if (e.code() == make_error_condition(io_errc::stream)) {
            cerr << "io_errc stream error condition" << endl;
        }
        else {
            cerr << "unmatched error condition code " << e.code() << endl;
        }
    }
}
```
