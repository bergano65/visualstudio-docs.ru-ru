---
title: "IDiaEnumSegments | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments - интерфейс"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перечисляет разные сегменты, содержащихся в источнике данных.  
  
## Синтаксис  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaEnumSegments`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Извлекает [интерфейс IEnumVARIANT](http://msdn.microsoft.com/ru-ru/139e3c93-faef-4003-9079-e0e94494db3e) версия данного перечислителя.|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Извлекает число сегментов.|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|Получает сегмент посредством индекса.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Извлекает заданное количество сегментов в последовательности перечисления.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Пропустить указанное количество сегментов в последовательности перечисления.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Сбросить последовательность перечисления в начало.|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод `QueryInterface` метод  [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объект.  См. пример.  
  
## Пример  
 В этом примере показано, как получить `IDiaEnumSections` интерфейс из таблицы.  Для более полного примера сегментов использования см. в разделе [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) интерфейс.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)