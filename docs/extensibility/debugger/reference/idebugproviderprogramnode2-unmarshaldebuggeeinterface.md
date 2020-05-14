---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720704"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Получает определенный интерфейс через границы процесса.

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
(в) GUID интерфейса для получения.

`ppvObject`\
(ваут) Возвращает объект, реализующий нужный интерфейс. Это может быть отлито непосредственно к желаемому типу интерфейса. «C» использовать <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод, чтобы получить желаемый интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется, когда отладка [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] двигателя работает в пространстве процесса и отладка программы работает в своем собственном пространстве процесса.

## <a name="see-also"></a>См. также
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
