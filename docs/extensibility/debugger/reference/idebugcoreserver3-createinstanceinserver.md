---
title: IDebugCoreServer3::CreateInstanceInServer | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 171eda8b7c1b206ea54839366686ad43f690afe0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886478"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Создает экземпляр модуля отладки на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
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