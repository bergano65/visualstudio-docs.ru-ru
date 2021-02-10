---
title: 'IDebugAlias2:: Жетаппдомаинид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c50473e12399e3977de55e67c7251d5783eecfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947129"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Возвращает идентификатор для домена приложения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Параметры
`pappDomainId`\
заполняет Возвращает идентификатор домена приложения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор домена приложения изменяется при каждом перезапуске приложения и создании нового домена приложения.

## <a name="see-also"></a>См. также раздел
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
