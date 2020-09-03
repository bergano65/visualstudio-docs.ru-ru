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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736414"
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
