---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40d52c5eedf0defb845f1944acd166d48dca1ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338163"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Извлекает идентификатор для домена приложения.

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
[out] Возвращает идентификатор домена приложения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Изменение идентификатора домена приложения при каждом перезапуске приложения, а также новый домен приложения создается.

## <a name="see-also"></a>См. также
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)