---
title: "freopen, _wfreopen"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - freopen
  - _wfreopen
apilocation: 
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
  - api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: 25
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# freopen, _wfreopen
Reassigns a file pointer. More secure versions of these functions are available; see [freopen_s, _wfreopen_s](../VS_visualcpp/freopen_s--_wfreopen_s.md).  
  
## Syntax  
  
```  
FILE *freopen(   
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
FILE *_wfreopen(   
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### Parameters  
 `path`  
 Path of new file.  
  
 `mode`  
 Type of access permitted.  
  
 `stream`  
 Pointer to `FILE` structure.  
  
## Return Value  
 Each of these functions returns a pointer to the newly opened file. If an error occurs, the original file is closed and the function returns a `NULL` pointer value. If `path`, `mode`, or `stream` is a null pointer, or if `filename` is an empty string, these functions invoke the invalid parameter handler, as described in [Parameter Validation](../VS_visualcpp/Parameter-Validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL` and return `NULL`.  
  
 See [_doserrno, errno, _sys_errlist, and _sys_nerr](../VS_visualcpp/errno--_doserrno--_sys_errlist--and-_sys_nerr.md) for more information on these, and other, error codes.  
  
## Remarks  
 More secure versions of these functions exist, see [freopen_s, _wfreopen_s](../VS_visualcpp/freopen_s--_wfreopen_s.md).  
  
 The `freopen` function closes the file currently associated with `stream` and reassigns `stream` to the file specified by `path`*.* `_wfreopen` is a wide-character version of `_freopen`; the `path` and `mode` arguments to `_wfreopen` are wide-character strings. `_wfreopen` and `_freopen` behave identically otherwise.  
  
### Generic-Text Routine Mappings  
  
|TCHAR.H routine|_UNICODE & _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen`|`freopen`|`freopen`|`_wfreopen`|  
  
 `freopen` is typically used to redirect the pre-opened files `stdin`, `stdout`, and `stderr` to files specified by the user. The new file associated with `stream` is opened with `mode`*,* which is a character string specifying the type of access requested for the file, as follows:  
  
 `"r"`  
 Opens for reading. If the file does not exist or cannot be found, the `freopen` call fails.  
  
 `"w"`  
 Opens an empty file for writing. If the given file exists, its contents are destroyed.  
  
 `"a"`  
 Opens for writing at the end of the file (appending) without removing the EOF marker before writing new data to the file; creates the file first if it does not exist.  
  
 `"r+"`  
 Opens for both reading and writing. (The file must exist.)  
  
 `"w+"`  
 Opens an empty file for both reading and writing. If the given file exists, its contents are destroyed.  
  
 `"a+"`  
 Opens for reading and appending; the appending operation includes the removal of the EOF marker before new data is written to the file and the EOF marker is restored after writing is complete; creates the file first if it does not exist.  
  
 Use the `"w"` and `"w+"` types with care, as they can destroy existing files.  
  
 When a file is opened with the `"a"` or `"a+"` access type, all write operations take place at the end of the file. Although the file pointer can be repositioned using `fseek` or `rewind`, the file pointer is always moved back to the end of the file before any write operation is carried out. Thus, existing data cannot be overwritten.  
  
 The `"a"` mode does not remove the EOF marker before appending to the file. After appending has occurred, the MS-DOS TYPE command only shows data up to the original EOF marker and not any data appended to the file. The `"a+"` mode does remove the EOF marker before appending to the file. After appending, the MS-DOS TYPE command shows all data in the file. The `"a+"` mode is required for appending to a stream file that is terminated with the CTRL+Z EOF marker.  
  
 When the `"r+"`, `"w+"`, or `"a+"` access type is specified, both reading and writing are allowed (the file is said to be open for "update"). However, when you switch between reading and writing, there must be an intervening [fsetpos](../VS_visualcpp/fsetpos.md), [fseek](../VS_visualcpp/fseek--_fseeki64.md), or [rewind](../VS_visualcpp/rewind.md) operation. The current position can be specified for the `fsetpos` or `fseek` operation, if desired. In addition to the above values, one of the following characters may be included in the `mode` string to specify the translation mode for new lines.  
  
 `t`  
 Open in text (translated) mode; carriage return–linefeed (CR-LF) combinations are translated into single linefeed (LF) characters on input; LF characters are translated to CR-LF combinations on output. Also, CTRL+Z is interpreted as an end-of-file character on input. In files opened for reading or for writing and reading with `"a+"`, the run-time library checks for a CTRL+Z at the end of the file and removes it, if possible. This is done because using `fseek` and `ftell` to move within a file may cause `fseek` to behave improperly near the end of the file. The `t` option is a Microsoft extension that should not be used where ANSI portability is desired.  
  
 `b`  
 Open in binary (untranslated) mode; the above translations are suppressed.  
  
 If `t` or `b` is not given in `mode`, the default translation mode is defined by the global variable [_fmode](../VS_visualcpp/_fmode.md). If `t` or `b` is prefixed to the argument, the function fails and returns `NULL`.  
  
 For a discussion of text and binary modes, see [Text and Binary Mode File I/O](../VS_visualcpp/Text-and-Binary-Mode-File-I-O.md).  
  
## Requirements  
  
|Function|Required header|  
|--------------|---------------------|  
|`freopen`|<stdio.h>|  
|`_wfreopen`|<stdio.h> or <wchar.h>|  
  
 The console is not supported in Windows 8.x Store apps. The standard stream handles that are associated with the console—`stdin`, `stdout`, and `stderr`—must be redirected before C run-time functions can use them in Windows 8.x Store apps. For additional compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md).  
  
## Example  
  
```  
// crt_freopen.c  
// compile with: /W3  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   // Reassign "stderr" to "freopen.out":   
   stream = freopen( "freopen.out", "w", stderr ); // C4996  
   // Note: freopen is deprecated; consider using freopen_s instead  
  
   if( stream == NULL )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
 **successfully reassigned**  
**This will go to the file 'freopen.out'**   
## .NET Framework Equivalent  
  
-   <xref:System.IO.File.Open?qualifyHint=False>  
  
-   <xref:System.IO.FileStream.#ctor?qualifyHint=False>  
  
## See Also  
 [Stream I/O](../VS_visualcpp/Stream-I-O.md)   
 [fclose, _fcloseall](../VS_visualcpp/fclose--_fcloseall.md)   
 [_fdopen, _wfdopen](../VS_visualcpp/_fdopen--_wfdopen.md)   
 [_fileno](../VS_visualcpp/_fileno.md)   
 [fopen, _wfopen](../VS_visualcpp/fopen--_wfopen.md)   
 [_open, _wopen](../VS_visualcpp/_open--_wopen.md)   
 [_setmode](../VS_visualcpp/_setmode.md)