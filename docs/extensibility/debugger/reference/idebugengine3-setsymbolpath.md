---
title: "IDebugEngine3::SetSymbolPath | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8cc60a266a238ee8d3635637b907ce88933b29a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Задает путь или пути, производится поиск символов отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Строка, содержащая путь поиска символов или пути. Дополнительные сведения в разделе «Примечания». Не может иметь значение NULL.|  
|`szSymbolCachePath`|[in] Строка, содержащая локальный путь, где можно кэшировать символы. Не может иметь значение NULL.|  
|`Flags`|[in] Не используется. всегда равен 0.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Строка `szSymbolSearchPath` приведен список один или несколько путей, разделенных точкой с запятой, для поиска символов. Эти пути может быть локальный путь, URL-адрес или путь UNC-стиля. Эти пути можно также сочетание разных типов. Если путь UNC (например, \\\Symserver\Symbols), а затем модуль отладки следует определить ли путь на сервере символов и должен иметь возможность загрузить символы с этого сервера, кэшируя их в каталоге, указанном `szSymbolCachePath`.  
  
 Путь к символам, также может содержать одно или несколько расположений кэша. Кэши первыми в порядке приоритета, с наивысшим приоритетом кэша и разделены * символы. Пример:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) метод выполняет реальную нагрузку символов.  
  
## <a name="see-also"></a>См. также  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)