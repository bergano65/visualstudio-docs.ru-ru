---
title: "Метод IJsDebugProcess::CreateBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод IJsDebugProcess::CreateBreakPoint
Задает точку останова в позиции указанного документа.  
  
## Синтаксис  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### Параметры  
 `documentId`  
 \[in\] Указатель на IDebugDocumentText.  
  
 `characterOffset`  
 \[in\] Смещение символов от начала файла.  
  
 `characterCount`  
 \[in\] Длина текста документа, в пределах которой необходимо вставить точку останова.  
  
 `isEnabled`  
 \[in\] Указывает, включена ли точка останова.  
  
 `ppDebugBreakPoint`  
 \[out\] Объект, представляющий точку останова, которая была создана.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)