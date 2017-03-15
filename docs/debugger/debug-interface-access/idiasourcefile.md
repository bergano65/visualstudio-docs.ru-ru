---
title: "IDiaSourceFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSourceFile - интерфейс"
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSourceFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Представляет исходный файл.  
  
## Синтаксис  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaSourceFile`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaSourceFile::get\_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Получает простое значение ключа целое число, являющееся уникальным для этого образа.|  
|[IDiaSourceFile::get\_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Возвращает имя файла источника.|  
|[IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Извлекает тип контрольной суммы.|  
|[IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Извлекает перечислитель compilands с номера линии, ссылающийся на этот файл.|  
|[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Возвращает байты контрольной суммы.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) OR  [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) методы.  См. пример.  
  
## Пример  
 Эта функция отображает имена всех исходных файлов, содержащий подставляемые в указанной таблице.  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)   
 [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)