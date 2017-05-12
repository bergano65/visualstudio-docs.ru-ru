---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
Определяет, если вызывающий объект обработчика скрипта может обработать определенное исключение.  
  
## Синтаксис  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### Параметры  
 `pExcepInfo`  
 \[in\] указатель на структуру, содержащую сведения, `EXCEPINFO` будет отмечено, если ни один обработчик исключения не найден.  
  
 `pvar`  
 \[in\] значение, связанное с исключением, выпиской как значение, созданное `throw`.  Этот параметр может иметь значение `NULL`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Вызывающий объект может обрабатывать исключение|  
|`E_FAIL`|Вызывающий объект не может обработать исключение.|  
  
## Заметки  
 Если вызов `IDispatchEx::InvokeEx` или аналогичного результата можно добиться, приводят к исключению, проверки jet скрипта для вызывающего объекта в цепочке вызывающего объекта скрипта, которая поддерживает интерфейс `ICanHandleException` и указывает на то, что он может обрабатывать исключение.  Если вызывающий объект не может обрабатывать исключение, то обработчик скриптов останавливает.  
  
## См. также  
 [Интерфейс ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)