---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::put_registerValue - метод"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Устанавливает значение регистра.  
  
## Синтаксис  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Параметры  
 `index`  
 \[in\] значение из [Перечисление CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, указывающее регистр для записи.  
  
 `NewVal`  
 \[in\] новое значение регистра.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Несмотря на размер значения, реализация должна содержать только что обычно сохраняет регистр.  Например, регистрация держал мере 8 \(sp2\) только самые низкие 8 бит заданного значения.  
  
## См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)