---
title: 'IDebugProviderProgramNode2:: Унмаршалдебугжееинтерфаце | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720704"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
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

## <a name="parameters"></a>Параметры
`riid`\
окне Идентификатор GUID получаемого интерфейса.

`ppvObject`\
заполняет Возвращает объект, реализующий нужный интерфейс. [C++] это можно привести непосредственно к нужному типу интерфейса. [C#] используйте <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод, чтобы получить нужный интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод используется, когда модуль отладки выполняется в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пространстве процесса, а отлаживаемая программа выполняется в собственном пространстве процесса.

## <a name="see-also"></a>См. также раздел
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
