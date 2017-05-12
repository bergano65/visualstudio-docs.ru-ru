---
title: "IRemoteDebugApplicationThreadEx:EnumGlobalContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThreadEx:EnumGlobalContexts"
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplicationThreadEx:EnumGlobalContexts
Перечисляет глобальные контекстах выражения для всех языков, выполняющиеся в этом потоке.  
  
## Синтаксис  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] перечислитель, который содержит глобальные контекстах выражения для всех языков, выполняющиеся в этом потоке.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки