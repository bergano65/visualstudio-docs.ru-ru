---
title: 'IDebugProviderProgramNode2:: Унмаршалдебугжееинтерфаце | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3007d13ec3eae46511e4775497d0aad5b6325b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146252"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает указанный интерфейс между границами процесса.  
  
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
 окне Идентификатор GUID получаемого интерфейса.  
  
 `ppvObject`  
 заполняет Возвращает объект, реализующий нужный интерфейс. [C++] это можно привести непосредственно к нужному типу интерфейса. [C#] используйте <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод, чтобы получить нужный интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод используется, когда модуль отладки выполняется в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пространстве процесса, а отлаживаемая программа выполняется в собственном пространстве процесса.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
