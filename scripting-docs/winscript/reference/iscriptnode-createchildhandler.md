---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
Добавляет сценарий, как экземпляр дочернего элемента `IScriptNode`.  
  
## Синтаксис  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### Параметры  
 `pszDefaultName`  
 \[in\] адрес имя по умолчанию, связанное со скриптом.  
  
 `prgpszNames`  
 \[in, size\_is \(`cpszNames`\)\] Список идентификаторов из полного имени на узле.  
  
 `cpszNames`  
 \[in\] количество идентификаторов в параметре `prgpszNames`.  
  
 `pszEvent`  
 \[in\] адрес буфера, указывающее имя события, связанные со скриптом.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  Для анализа, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец блока скрипта.  
  
 Разделитель включает предварительная обработка скриптом создания обработчика.  Например, обработчик может заменить одинарная кавычка с 2 одинарными кавычками для использования в качестве разделителя.  Обработчик задает в качестве разделителя используется.  
  
 Задайте значение null, если разделитель не используется для указания конец блока скрипта.  
  
 `ptiSignature`  
 \[in\] сведения о типе объекта функции.  
  
 `iMethodSignature`  
 \[in\] индекс функции в параметре `ITypeInfo``ptiSignature`.  
  
 `isn`  
 \[in\] индекс дочернего элемента в родительском элементе.  
  
 `dwCookie`  
 \[in\] приложение\- указанное значение, которое используется для связывания запись с объектом основного приложения.  
  
 `ppse`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IScriptEntry` экземпляра дочернего элемента.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Скрипт определяет обработчик событий.  Этот метод создает скрипт, если Позвонитьо объектом, `IScriptNode`, представляющий страницу.  Этот метод не выполняется успешно, если он вызывается другими интерфейсами.  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)