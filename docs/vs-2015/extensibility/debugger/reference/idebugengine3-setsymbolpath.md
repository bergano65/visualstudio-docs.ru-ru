---
title: 'IDebugEngine3:: Сетсимболпас | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476797"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает путь или пути, по которым выполняется поиск отладочных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
|Параметр|Description|  
|---------------|-----------------|  
|`szSymbolSearchPath`|окне Строка, содержащая путь поиска символов или пути. Дополнительные сведения см. в разделе "Примечания". Не может иметь значение null.|  
|`szSymbolCachePath`|окне Строка, содержащая локальный путь, по которому можно кэшировать символы. Не может иметь значение null.|  
|`Flags`|окне Не используется; всегда имеет значение 0.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Строка `szSymbolSearchPath` представляет собой список из одного или нескольких путей, разделенных точкой с запятой, для поиска символов. Эти пути могут быть локальным путем, UNC-путем или URL-адресом. Эти пути также могут быть смесью различных типов. Если путь имеет формат UNC (например, \\\Симсервер\симболс), то модуль отладки должен определить, является ли путь сервером символов и должен ли он быть способен загружать символы с этого сервера, а затем кэшировать их по пути, указанному в `szSymbolCachePath`.  
  
 Путь к символам также может содержать одно или несколько расположений кэша. Кэши перечисляются в порядке приоритета, сначала используется кэш с наивысшим приоритетом, который отделяется символами *. Пример:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 Метод [лоадсимболс](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) выполняет фактическую загрузку символов.  
  
## <a name="see-also"></a>См. также:  
 [Лоадсимболс](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
