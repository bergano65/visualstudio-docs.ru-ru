---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
Возвращает перечислитель кадров стека текущего потока.  
  
## Синтаксис  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Параметры  
 `dwSpMin`  
 \[in\] меньшее ограничение адресов для перечисления кадры стека.  
  
 `ppedsf`  
 \[out\] перечислитель кадров стека текущего потока.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Перечислитель кадра стека возвращает кадров в верхней части стека, начиная с последнего отправлянным кадром.  Перечислитель содержит только кадры стека с адресом " больше или равно `dwSpMin`.  
  
## См. также  
 [Интерфейс IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)