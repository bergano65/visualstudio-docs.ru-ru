---
title: "IDiaSegment | Microsoft Docs"
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
  - "IDiaSegment - интерфейс"
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaSegment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Данные сопоставления из номера секции к сегментам адресного пространства.  
  
## Синтаксис  
  
```  
IDiaSegment : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaSegment`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaSegment::get\_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Извлекает число сегментов.|  
|[IDiaSegment::get\_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Получает смещение в сегментах где раздел.|  
|[IDiaSegment::get\_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Извлекает число байтов в сегменте.|  
|[IDiaSegment::get\_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Извлекает пометить, указывающее, является ли сегмент можно считать.|  
|[IDiaSegment::get\_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Извлекает пометить, указывающее, является ли сегмент может быть изменен.|  
|[IDiaSegment::get\_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Извлекает пометить, указывающее, является ли сегмент исполнительн.|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Получает номер секции, который сопоставляет на этот сегмент.|  
|[IDiaSegment::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Получает относительный виртуальный адрес RVA\) \(начальной секции.|  
|[IDiaSegment::get\_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Получает виртуальный адрес \(\) VA начальной секции.|  
  
## Заметки  
 Поскольку пакет SDK для доступа к интерфейсу отладки еще выполняет преобразование из раздела с относительным виртуальным адресам смещения, большинство приложений не используют сведения в сопоставлении сегмента.  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md) OR  [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) методы.  См. пример.  
  
## Пример  
 Эта функция отображает адрес всех сегментов в таблице и закрыть символе.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
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
 [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)