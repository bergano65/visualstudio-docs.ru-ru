---
title: "Перечисление ERRORRESUMEACTION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION — перечисление"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Перечисление ERRORRESUMEACTION
Описывает, как продолжить из продолжающей погрешности.  
  
## Синтаксис  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Члены  
  
|Элемент|Описание|  
|-------------|--------------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|Re\- выполняет выписка, вызвавшее ошибку.|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|Позволяет обработчику языка обработки ошибки.|  
|ERRORRESUMEACTION\_SkipErrorStatement|Возобновляет выполнение в коде, за которым следует выпиской, вызвавшее ошибку.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)