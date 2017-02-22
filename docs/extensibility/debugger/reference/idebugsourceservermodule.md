---
title: "IDebugSourceServerModule | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugSourceServerModule"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет сведения о сервере источника, в котором содержится в файле PDB.  
  
## Синтаксис  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется и используется командами отладки пользовательский интерфейс отладчика.  
  
## Методы  
 В следующей таблице показаны методы `IDebugSourceServerModule`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив данных сервера источника.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll