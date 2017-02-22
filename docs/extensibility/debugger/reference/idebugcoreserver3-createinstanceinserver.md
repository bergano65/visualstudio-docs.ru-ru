---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
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
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает экземпляр обработчика отладки на сервере.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### Параметры  
 `szDll`  
 \[in\] путь к dll\-библиотеке, реализующей CLSID, определенные в `clsidObject` параметр.  Если данное `NULL`после этого модель COM  `CoCreateInstance` функция вызвана.  
  
 `wLangId`  
 \[in\] языковой стандарт обработчика отладки.  Это может быть 0, если [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) метод не должен вызываться.  
  
 `clsidObject`  
 \[in\] идентификатор CLSID обработчика отладки, которые необходимо создать.  
  
 `riid`  
 \[in\] идентификатор интерфейса конкретного интерфейса, извлекаемого из объекта класса.  
  
 `ppvObject`  
 \[out\] `IUnknown` интерфейс из экземпляра объекта.  Приведение или маршалируйте этот объект к требуемому интерфейсу.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)