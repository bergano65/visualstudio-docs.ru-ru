---
title: "IDiaLineNumber | Microsoft Docs"
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
  - "IDiaLineNumber - интерфейс"
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLineNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Обращается к сведения, описывающие процесс сопоставления из блока байтов текст образа на номер линии исходного файла.  
  
## Синтаксис  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaLineNumber`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaLineNumber::get\_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|Извлекает ссылку на символ для compiland, использованное байты текст образа.|  
|[IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)|Извлекает ссылку на объект из исходного файла.|  
|[IDiaLineNumber::get\_lineNumber](../Topic/IDiaLineNumber::get_lineNumber.md)|Получает номер линии в файле источника.|  
|[IDiaLineNumber::get\_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|Получает смещение номер линии источника, когда оператор или выражение.|  
|[IDiaLineNumber::get\_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|Получает номер столбца, в котором начинается выражение или оператор.|  
|[IDiaLineNumber::get\_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|Получает номер столбца, в котором выражение или оператор.|  
|[IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|Извлекает часть раздела адреса памяти, где начинается блок.|  
|[IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|Извлекает часть смещения адреса памяти, где начинается блок.|  
|[IDiaLineNumber::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|Получает относительный виртуальный адрес образа \(RVA\) блока.|  
|[IDiaLineNumber::get\_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|Получает виртуальный адрес \(VA\) блока.|  
|[IDiaLineNumber::get\_length](../Topic/IDiaLineNumber::get_length.md)|Извлекает число байтов в блоке.|  
|[IDiaLineNumber::get\_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|Извлекает уникальный идентификатор исходного файла для файла источника, способствовал эту линию.|  
|[IDiaLineNumber::get\_statement](../Topic/IDiaLineNumber::get_statement.md)|Извлекает пометить указывающее, что эти данные линий, описывающих начало выписки в источнике программы.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Извлекает уникальный идентификатор для compiland, использованное эту линию.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) OR  [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) методы.  
  
## Пример  
 Следующие номера выделительнаяа строка функции, используемые в функции \(представленных by `pSymbol`\).  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)