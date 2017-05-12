---
title: "Определение типа (Typedef) JsRef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Определение типа (Typedef) JsRef
Ссылка на объект, относящийся к сборщику мусора Chakra.  
  
## Синтаксис  
  
```  
typedef void *JsRef;  
```  
  
## Заметки  
 Среда выполнения Chakra будет автоматически отслеживать ссылки JsRef, пока они хранятся в локальных переменных или в параметрах \(например,  в стеках\).  Чтобы хранить JsRef где\-либо, кроме стека, необходимо вызывать методы JsAddRef и JsRelease, управляющие временем существованием объекта. В противном случае сборщик мусора может освободить объект, даже если он еще используется.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)