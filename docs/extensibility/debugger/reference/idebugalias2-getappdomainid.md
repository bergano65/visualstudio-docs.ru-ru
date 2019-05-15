---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17f6e487dee1b5ae490cfc2ab180eb872ed5b5d2
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615098"
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