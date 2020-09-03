---
title: 'IDebugCoreServer3:: Креатеинстанцеинсервер | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
 окне Путь к библиотеке DLL, реализующей CLSID, указанный в `clsidObject` параметре. Если это так `NULL` , то `CoCreateInstance` вызывается функция com.  
  
 `wLangId`  
 окне Языковой стандарт модуля отладки. Это значение может быть равно 0, если метод [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) не должен вызываться.  
  
 `clsidObject`  
 окне CLSID создаваемого модуля отладки.  
  
 `riid`  
 окне Идентификатор интерфейса конкретного интерфейса, который необходимо получить из объекта класса.  
  
 `ppvObject`  
 [out] `IUnknown` интерфейс из созданного объекта. Приведите или маршалирует этот объект к нужному интерфейсу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [Pragma](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
