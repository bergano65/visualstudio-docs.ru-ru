---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables - интерфейс"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Перечисляет различные таблицы, содержащихся в источнике данных.  
  
## Синтаксис  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDiaEnumTables`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Извлекает [интерфейс IEnumVARIANT](http://msdn.microsoft.com/ru-ru/139e3c93-faef-4003-9079-e0e94494db3e) версия данного перечислителя.|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Получает количество таблиц.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Извлекает таблицу с помощью индекса или имени.|  
|[IDiaEnumTables::Next](../Topic/IDiaEnumTables::Next.md)|Извлекает заданное количество таблиц в последовательности перечисления.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Пропустить указанное количество таблиц в последовательности перечисления.|  
|[IDiaEnumTables::Reset](../Topic/IDiaEnumTables::Reset.md)|Сбросить последовательность перечисления в начало.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## Заметки  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) метод.  
  
## Пример  
 В этом примере показано, как получить `IDiaEnumTables` интерфейс из сеанса.  Для более полного примера таблиц использования см. в разделе [IDiaTable](../../debugger/debug-interface-access/idiatable.md) интерфейс.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)