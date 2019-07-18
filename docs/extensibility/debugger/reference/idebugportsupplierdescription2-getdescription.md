---
title: IDebugPortSupplierDescription2::GetDescription | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7619421e66b8f6e68c252fd2c2885272003bb6e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339942"
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
Извлекает описания и описание метаданных поставщика порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDescription(
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,
   BSTR *pbstrText
);
```

```csharp
public int GetDescription(
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,
   out string pbstrText
);
```

## <a name="parameters"></a>Параметры
`pdwFlags`\
[out] Флаги метаданных для описания.

`pbstrText`\
[out] Описание поставщика порта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)