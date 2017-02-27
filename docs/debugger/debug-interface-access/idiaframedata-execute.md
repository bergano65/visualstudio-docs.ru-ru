---
title: "IDiaFrameData::execute | Microsoft Docs"
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
  - "IDiaFrameData::execute - метод"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Выполняет стек разматывая и возвращает результаты в интерфейсе кадра проверки стека.  
  
## Синтаксис  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Параметры  
 `frame`  
 \[in\] [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) объект, содержащий состояние кадра регистрирует.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены возможные возвращаемые значения для данного метода.  
  
|Значение|Описание|  
|--------------|--------------|  
|E\_DIA\_INPROLOG|Не удается выполнить кадр стека в коде пролога.|  
|E\_DIA\_SYNTAX|Ошибка синтаксического анализа обнаружена в программе кадра.|  
|E\_DIA\_FRAME\_ACCESS|Не удалось получить доступ к памяти или регистров.|  
|E\_DIA\_VALUE|Ошибка при вычислении значения \(например, отделении нуля\).|  
  
## Заметки  
 Этот метод вызывается во время отладки для очистки последнего маркера стек.  [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) объект реализуется клиентским приложением получить обновления к регистрам и предоставлять методы, предназначенные  `execute` метод.  
  
## См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)