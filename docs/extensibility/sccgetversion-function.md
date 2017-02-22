---
title: "Функция SccGetVersion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "Функция SccGetVersion"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccGetVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция возвращает номер версии API подключаемого модуля управления источника, поддерживаемых подключаемым модулем системы управления версиями.  
  
## Синтаксис  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### Параметры  
 Отсутствует.  
  
## Возвращаемое значение  
 A `LONG` тип данных, который содержит номер версии поддерживаемых API подключаемого модуля управления источника:  
  
|WORD|Описание|  
|----------|--------------|  
|HIWORD|Основной номер версии|  
|LOWORD|Дополнительный номер версии|  
  
## Заметки  
 Например если подключаемый модуль системы управления версиями поддерживает версии 1.3 API подключаемого модуля управления источника, эта функция вернет 0x0103.  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)