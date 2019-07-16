---
title: IDebugCoreServer3::CreateInstanceInServer | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1d8964a79aaeb7b90dfbc809ec547d0282d79fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205268"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает экземпляр модуля отладки на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
