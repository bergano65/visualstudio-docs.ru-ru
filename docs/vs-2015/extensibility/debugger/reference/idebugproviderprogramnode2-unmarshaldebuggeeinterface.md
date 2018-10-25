---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d90a0406d5325ee11ec5c6230110128abc14de5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893368"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 [in] Идентификатор GUID интерфейса для получения.  
  
 `ppvObject`  
 [out] Возвращает объект, реализующий требуемого интерфейса. [C++] это может быть приведен непосредственно в тип требуемого интерфейса. [C#] используйте <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения требуемого интерфейса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется в том случае, если отладчик работает в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пространство процесса и отлаживаемой программы выполняется в свое собственное пространство процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)

