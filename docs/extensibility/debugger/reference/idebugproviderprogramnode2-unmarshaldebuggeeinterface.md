---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86c20e7c6828cfbf3ec31ba5dcbec9c7ee8478df
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706227"
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
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)