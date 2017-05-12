---
title: "IScriptNode::CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode::CreateChildEntry
Добавляет экземпляр дочернего элемента `IScriptEntry`.  
  
## Синтаксис  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### Параметры  
 `isn`  
 \[in\] индекс дочернего элемента в родительском элементе.  
  
 `dwCookie`  
 \[in\] приложение\- указанное значение, используемое для связывания запись дочернего элемента с объектом основного приложения.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  Для анализа, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец блока скрипта.  
  
 Разделитель включает в скрипт создание обработчика для предоставления предварительная обработка.  Например, обработчик может заменить одинарная кавычка с 2 одинарными кавычками для использования в качестве разделителя.  Обработчик задает в качестве разделителя используется.  
  
 Задайте значение null, если разделитель не отмечает конец блока скрипта.  
  
 `ppse`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IScriptEntry` экземпляра дочернего элемента.  
  
 Для объектов `IScriptNode`, представляющие страницу, передачи этого параметра экземпляр `IScriptEntry`, определяющий блок скрипта.  
  
 Для объектов, которые представляют блоки скрипта, `IScriptEntry` получения этого параметра экземпляр, определяющий объект `IScriptEntry` функции.  
  
 Для объектов `IScriptEntry`, представляющие объект функции, происходит сбой метода.  
  
 Для объектов `IScriptScriptlet` этот метод завершается ошибкой.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Интерфейс `IScriptNode` представляет страницу или его элементы.  Интерфейс `IScriptEntry` \(производный от `IScriptNode`\) представляет блок скрипта или функции.  Интерфейс `IScriptScriptlet` \(производный от `IScriptEntry`\) представляет обработчик событий.  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)