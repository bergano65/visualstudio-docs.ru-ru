---
title: "Метод IJsDebugDataTarget::CreateStackFrameEnumerator | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation: jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::CreateStackFrameEnumerator
Создает перечислитель для кадров стека.  
  
## Синтаксис  
  
```  
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### Параметры  
 `threadId`  
 \[in\] Поток, выполняемый в целевом процессе.  
  
 `ppEnumerator`  
 \[out\] Перечислитель для кадров стека.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)