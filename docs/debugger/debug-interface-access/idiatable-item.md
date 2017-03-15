---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "IDiaTable::Item - метод"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает ссылку на определенной записи в таблице.  
  
## Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Параметры  
 `index`  
 \[in\] индекс записи в диапазоне от 0 до таблицы `count`\-1, где  `count` возвращает   [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)метод.  
  
 `element`  
 \[out\] возвращает `IUnknown` объект, представляющий запись указанной таблицы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Таблица представляет собой коллекцию объектов.  В зависимости от объектов, параметр элемента может быть приведен к соответствующему интерфейсу.  Например, если таблица содержит [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) объекты, затем параметр элемента может быть приведен к  `IDiaSegment` интерфейс.  
  
 Более общий подход, вызываемый `QueryInterface` метод  [IDiaTable](../../debugger/debug-interface-access/idiatable.md) интерфейс для соответствующего интерфейса перечислителя и использует методы, определенные для доступа к содержимому таблицы.  См. [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) интерфейс для примера.  
  
## См. также  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)