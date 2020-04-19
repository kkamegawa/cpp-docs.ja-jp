---
title: ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: 763d76dd9eb139c10f4147e5fa069a0901fe5398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188383"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数

多くの C ランタイム (CRT) 関数はユニバーサル Windows プラットフォーム (UWP) アプリをビルドする時に使用できません。 場合によっては、回避策がある--たとえば、Windows ランタイムまたは Win32 Api を使用できます。 しかし、回避策が利用できない場合には、CRT 関数は禁止されています。CRT 関数に相当する機能やサポートする API を UWP アプリに使用できないためです。 Windows ランタイムのサポートされている別の方法を探すを参照してください。 [UWP アプリでの Windows Api の代替](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)します。

次の一覧には UWP アプリをビルドするときに使用できない CRT 関数と、その回避策があればそれを示しています。

## <a name="unsupported-crt-functions"></a>サポートされない CRT 関数

||||
|-|-|-|
|_beep _sleep _seterrormode|これらの関数は以前のバージョンの CRT で廃止されています。 また、それに対応する Win32 API は UWP アプリでは使用できません。|回避策はありません。|
|chdir _chdrive getcwd|これらの関数は廃止されているか、またはスレッド セーフではありません。|_chdir、_getcwd、関連する関数を使用します。|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|これらの関数は、コンソールから直接読み取ったり、コンソールに直接書き込んだりするときに使用されます。 UWP アプリは GUI のみであり、コンソールをサポートしていません。|回避策はありません。|
|getpid|これは古い関数です。|_getpid または Win32 API `GetCurrentProcessId()`を使用します。|
|_getdiskfree|使用できません。|Win32 API `GetDiskFreeSpaceExW()`を使用します。|
|_getdrive _getdrives|対応する API はUWP アプリでは使用できません。|回避策はありません。|
|_inp _inpd _inpw _outp _outpd _outpw inp inpd inpw outp outpd outpw|ポート IO は UWP アプリではサポートされていません。|回避策はありません。|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|マルチバイト文字列はUWP アプリではサポートされていません。|代わりに、Unicode 文字列を使用します。|
|_pclose _pipe _popen _wpopen|パイプ機能は UWP アプリには使用できません。|回避策はありません。|
|_resetstkoflw|サポートする Win32 API は UWP アプリでは使用できません。|回避策はありません。|
|_getsystime _setsystime|これらは以前のバージョンの CRT で廃止された API です。 また、ユーザーはアクセス許可がないため、UWP アプリのシステム時刻を設定できません。|システム時刻のみを取得するには、Win32 API `GetSystemTime`を使用します。 システム時刻は設定できません。|
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|UWP アプリでは環境変数を使用できません。|回避策はありません。 タイム ゾーンを設定するには、_tzset を使用します。|
|_loaddll _getdllprocaddr _unloaddll|これらは以前のバージョンの CRT で廃止された関数です。 また、ユーザーは同じアプリケーション パッケージのものを除き、DLL を読み込むことができません。|パッケージ化された DLL を読み込んで使用するには、Win32 API `LoadPackagedLibrary`、 `GetProcAddress`、 `FreeLibrary` を使用します。|
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|この機能は、UWP アプリでは使用できません。 UWP アプリから別の UWP アプリまたはデスクトップ アプリを起動することはできません。|回避策はありません。|
|_heapwalk _heapadd _heapchk _heapset _heapused|ここに挙げた関数は通常、ヒープを使用するために使用します。 しかし、UWP アプリでは対応する Win32 API がサポートされていません。 アプリがプライベート ヒープを作成したり使用したりすることはありません。|回避策はありません。 ただし、 `_heapwalk` はデバッグを目的とする場合にのみ DEBUG CRT で使用できます。 これらは、Microsoft Store にアップロードされるアプリで使用することはできません。|

次の関数は、UWP アプリの CRT で使用できますが、対応する Win32 または Windows ランタイム Api を使用できない場合にのみ使用する必要があります: 大規模なコード ベースを移植する場合など、

|||
|-|-|
|1 バイト文字列関数 ( `strcat`、 `strcpy`、 `strlwr`など)。|UWP アプリには Unicode Unicode 文字セットのみを使用して、すべての Win32 Api と Windows ランタイム Api は公開されているためです。  1 バイトの関数は、大きなコード ベースを移植するときのために残されていますが、それ以外の状況では使用を避け、可能な限り対応するワイド文字関数を使用してください。|
|ストリーム IO 関数と低レベル ファイル IO 関数 ( `fopen`、 `open`など)。|ここに挙げた関数は同期的であるため、UWP アプリに使用することは勧められていません。 UWP アプリでは、UI スレッドがロックされることがないように、ファイルを開くとき、ファイルから読み取るとき、ファイルに書き込むときは非同期 API を使用します。 このような API には、 `Windows::Storage::FileIO` クラスのものなどが挙げられます。|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x ストア アプリと Windows Phone 8.x アプリ

前述した API に加えて、次の API を Windows 8.x ストア アプリと Windows Phone 8.x アプリで使用することはできません。

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|Windows 8.x ストア アプリで Win32 API をスレッド化することはできません。|代わりに `Windows Runtime Windows::System::Threading::ThreadPool` または `concurrency::task` を使用します。|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|作業ディレクトリの概念は Windows 8.x ストア アプリには適用されません。|代わりに完全パスを使用します。|
|_getpid|この関数は以前のバージョンの CRT で廃止されています。|Win32 API `GetCurrentProcessId()`を使用します。|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Windows 8.x ストア アプリではマルチバイト文字列がサポートされていません。|代わりに、Unicode 文字列を使用します。|
|_tzset|Windows 8.x ストア アプリでは環境変数を使用できません。|回避策はありません。|
|_get_heap_handle、_heapmin|Windows 8.x ストア アプリでは対応する Win32 API がサポートされません。 アプリでプライベート ヒープを作成できなくなりました。|回避策はありません。 ただし、 `_get_heap_handle` はデバッグを目的とする場合にのみ DEBUG CRT で使用できます。|