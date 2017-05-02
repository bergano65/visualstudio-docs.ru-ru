---
title: "Определение типа (Typedef) JsBackgroundWorkItemCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsBackgroundWorkItemCallback
Обратный вызов фонового рабочего элемента.  
  
## Синтаксис  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### Параметры  
 callbackData  
 Аргумент данных, передаваемый в службу потока.  
  
## Заметки  
 Аргумент передается в службу потока узла \(если есть\), что позволяет узлу осуществлять обратный вызов рабочего элемента на фоновом потоке по своему выбору.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)