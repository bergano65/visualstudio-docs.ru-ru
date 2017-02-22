---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::get_registerValue - метод"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает значение регистра.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Параметры  
 `index`  
 \[in\] значение из [Перечисление CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, указывающее, регистра для получения значения.  
  
 `pRetVal`  
 \[out\] возвращает текущее значение регистра.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Несмотря на размер `pRetVal` параметр реализация должен хранить только что обычно сохраняет регистр.  Например, регистрация содержит только 8 \(sp2\) самые низкие 8 бит заданного значения.  Это значение к 8 разрядное развернут 64 \(sp2\) возвращаемый из этого метода.  
  
## См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)