---
title: "IDiaSectionContrib | Microsoft Docs"
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
  - "IDiaSectionContrib - интерфейс"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает данные, описывающие вклад раздела, т е непрерывный блок памяти в способствованный образу compiland.  
  
## Синтаксис  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaSectionContrib`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Извлекает ссылку на символ compiland, способствовал в этом разделе.|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Извлекает часть раздела адреса вклада.|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Извлекает часть смещения адреса вклада.|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../Topic/IDiaSectionContrib::get_relativeVirtualAddress.md)|Получает относительный виртуальный адрес образа \(RVA\) вклада.|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Получает виртуальный адрес \(VA вклада.\)|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Извлекает число байтов в разделе.|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Извлекает пометить, указывающее, является ли раздел нельзя вызвать из памяти.|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Извлекает пометить указывающее, должен ли раздел не быть проложен к следующей границе памяти.|  
|[IDiaSectionContrib::get\_code](../Topic/IDiaSectionContrib::get_code.md)|Извлекает пометить, указывающее, содержит ли раздел исполняемый код.|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Извлекает пометить, указывающее, содержит ли раздел 16\-разрядный код.|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Извлекает пометить, указывающее, содержит ли раздел инициализированные данные.|  
|[IDiaSectionContrib::get\_uninitializedData](../Topic/IDiaSectionContrib::get_uninitializedData.md)|Извлекает пометить, указывающее, содержит ли раздел неинициализированные данные.|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Извлекает пометить указывающее, содержит ли раздел комментарии или аналогичное сведения.|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Извлекает пометить, указывающее, удален ли раздел, прежде чем он становится частью образа в памяти.|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Извлекает пометить раздела COMDAT, указывающее, является ли запись.|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Извлекает пометить, указывающее, может ли секция может быть отменено.|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Извлекает пометить, указывающее, может ли секция быть кэшироваться.|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Извлекает пометить, указывающее, является ли раздел может использоваться в памяти.|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Извлекает пометить, указывающее, является ли раздел исполнительн как код.|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Извлекает пометить, указывающее, является ли раздел можно считать.|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Извлекает пометить, указывающее, может ли секция может записать.|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Извлекает циклическую проверку избыточности \(CRC\) данных в шаге.|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Извлекает CRC данных перемещения для секции.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Извлекает идентификатор compiland для секции.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Этот интерфейс полученного вызовом метода [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) и  [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md) методы.  См. [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) интерфейс пример получения  `IDiaSectionContrib` интерфейс.  
  
## Пример  
 Эта функция отображает адрес каждого раздела вместе с всеми связанными символами.  См. [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) интерфейс для просмотра как  `IDiaSectionContrib` интерфейс получен.  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)