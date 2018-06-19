---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9ebadbc35ee8752e9f3b985a99155444caff5f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119754"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Получает указанный интерфейс через границы процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `riid`  
 [in] Идентификатор GUID интерфейса, для получения.  
  
 `ppvObject`  
 [out] Возвращает объект, реализующий нужного интерфейса. [C++] это может быть приведен типу нужного интерфейса. [C#] используйте <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения нужного интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется, когда отладчик работает в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пространство процесса и отлаживаемая программа выполняется в свое собственное пространство процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)