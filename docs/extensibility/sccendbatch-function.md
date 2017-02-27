---
title: "Функция SccEndBatch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "Функция SccEndBatch"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Функция SccEndBatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция завершается пакет операций системы управления версиями. Эти пакеты не могут быть вложенными.  
  
## Синтаксис  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### Параметры  
 Отсутствует.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Пакет успешно завершения операций.|  
|SCC\_E\_UNKNOWNERROR|Неспецифическая ошибка.|  
  
## Заметки  
 Пакеты управления источника используются для выполнения одной операции системы управления версиями для нескольких проектов или нескольких контекстов. Пакеты можно использовать во избежание избыточного диалоговые окна работу пользователей во время пакетной операции.[SccBeginBatch](../extensibility/sccbeginbatch-function.md) И `SccEndBatch` функции используются как пара для указания начала и окончания операции. Они не могут быть вложенными.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)