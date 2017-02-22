---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "Функция обратного вызова OPTNAMECHANGEPFN"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Это функция обратного вызова, указанный в вызове к [SccSetOption](../extensibility/sccsetoption-function.md) \(с помощью параметра `SCC_OPT_NAMECHANGEPFN`\) и используется для связи имени изменений, внесенных системы управления версиями подключаемого модуля в Интегрированной среде разработки.  
  
## Подпись  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## Параметры  
 pvCallerData  
 \[in\] Значение пользователя, указанного в предыдущем вызове [SccSetOption](../extensibility/sccsetoption-function.md) \(с помощью параметра `SCC_OPT_USERDATA`\).  
  
 pszOldName  
 \[in\] Исходное имя файла.  
  
 pszNewName  
 \[in\] Назовите файл был переименован в.  
  
## Возвращаемое значение  
 Отсутствует.  
  
## Заметки  
 Если файл переименовывается во время операции системы управления версиями, подключаемый модуль системы управления версиями может уведомить об изменении через этот обратный вызов интегрированной среды разработки.  
  
 Если интегрированная среда разработки не поддерживает этот обратный вызов, он не будет вызывать [SccSetOption](../extensibility/sccsetoption-function.md) для его указания. Если подключаемый модуль не поддерживает этот обратный вызов, он будет возвращать `SCC_E_OPNOTSUPPORTED` из `SccSetOption` работать при попытке задать обратный вызов интегрированной среды разработки.  
  
## См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)