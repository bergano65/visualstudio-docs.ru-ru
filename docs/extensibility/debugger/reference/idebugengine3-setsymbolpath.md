---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
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
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает путь или путь, искать символы отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|`szSymbolSearchPath`|\[in\] строка, которая содержит путь или путь поиска символа.  См. раздел "примечания".  Не может принимать значение NULL.|  
|`szSymbolCachePath`|\[in\] значение типа string, содержащее локальный путь, где символы могут кэшироваться.  Не может принимать значение NULL.|  
|`Flags`|\[in\] не используется; всегда задавайте значение 0.|  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 String`szSymbolSearchPath` список из одного или нескольких путей, разделенных точкой с запятой, для поиска символов.  Эти пути могут быть локальным путем с UNC\-стиля или url\-адреса.  Эти пути могут быть также смешиванием различных типов.  Если путь UNC \(например, \\ \\ Symserver \\ символов\), то отладчик должен определить, является ли путь к серверу символов и удается загрузить символы от сервера, то прячущ их в заданном пути: `szSymbolCachePath`.  
  
 Путь к символам также может содержать один или несколько расположений кэша.  Кэши перечислены в порядке приоритета, с кэшем наивысшим приоритетом во\-первых, и отделенными by \* символами.  Примеры.  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) метод выполняет фактическую загрузки символов.  
  
## См. также  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)