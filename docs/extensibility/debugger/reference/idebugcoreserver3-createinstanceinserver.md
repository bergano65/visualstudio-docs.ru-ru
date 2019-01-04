---
title: IDebugCoreServer3::CreateInstanceInServer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ea773179232115938657f8ccc1ee1accd525f87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841477"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Создает экземпляр модуля отладки на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `szDll`  
 [in] Путь к dll, реализующим CLSID, указанный в `clsidObject` параметра. Если это `NULL`, затем COM `CoCreateInstance` функция вызывается.  
  
 `wLangId`  
 [in] Языковой стандарт модуля отладки. Это может быть 0, если [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) не следует вызывать метод.  
  
 `clsidObject`  
 [in] CLSID для обработчика отладки, чтобы создать.  
  
 `riid`  
 [in] Идентификатор интерфейса указанного интерфейса для извлечения из объекта класса.  
  
 `ppvObject`  
 [out] `IUnknown` интерфейс из экземпляра объекта. Приведите или упаковывает и передает этот объект для требуемого интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)