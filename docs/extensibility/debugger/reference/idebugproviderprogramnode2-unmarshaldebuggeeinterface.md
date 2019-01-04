---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: c91ac932692ac63cfd4f8129fdff65993cddf2e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856112"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Получает указанный интерфейс через границы процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `riid`  
 [in] Идентификатор GUID интерфейса для получения.  
  
 `ppvObject`  
 [out] Возвращает объект, реализующий требуемого интерфейса. [C++] это может быть приведен непосредственно в тип требуемого интерфейса. [C#] использовать <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения требуемого интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется в том случае, если отладчик работает в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пространство процесса и отлаживаемой программы выполняется в свое собственное пространство процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)