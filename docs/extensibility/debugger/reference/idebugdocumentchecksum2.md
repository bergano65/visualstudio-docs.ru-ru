---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
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
  - "Интерфейс IDebugDocumentChecksum2"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет контрольную сумму для документа отладки, а также передача контрольную сумму между компонентами.  
  
## Синтаксис  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс может быть реализован любым компонентом, который предоставляет IDebugDocumentContext2 интерфейс.  Однако он главным образом реализуется следующими элементами привязки отладочные обработчики, чтобы контрольную сумму внедренную в файле символов \(\*.pdb\) можно передать обратно в интегрированной среде разработки и использования при поиске источник.  
  
## Методы  
 В следующей таблице показаны методы `IDebugDocumentChecksum2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Извлекает идентификатор контрольной суммы и алгоритма документа заданное максимальное число байтов, которое следует использовать.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll