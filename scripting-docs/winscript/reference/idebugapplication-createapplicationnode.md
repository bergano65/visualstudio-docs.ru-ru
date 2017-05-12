---
title: "IDebugApplication::CreateApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateApplicationNode"
ms.assetid: 1a1414f6-df14-4c56-b39a-8384cf16174a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateApplicationNode
Создает узел нового приложения, который связан с поставщиком заданного документа.  
  
## Синтаксис  
  
```  
HRESULT CreateApplicationNode(  
   IDebugApplicationNode**  ppdanNew  
);  
```  
  
#### Параметры  
 `ppdanNew`  
 \[out\] узел приложения, связанный с данным поставщиком документа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Узел нового приложения не отображается до тех пор, пока он не вложен в родительскому узлу.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)