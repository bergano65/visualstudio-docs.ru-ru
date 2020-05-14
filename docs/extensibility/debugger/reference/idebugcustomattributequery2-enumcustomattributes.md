---
title: IDebugCustomАтрибутыКЕRY2::EnumCustomАтрибуты (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732584"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Получает регистратор для всех пользовательских атрибутов, прикрепленных к этому полю.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugCustomAttributes,](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) представляющий список пользовательских атрибутов; в противном случае возвращает нулевую стоимость, если нет пользовательских атрибутов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или S_FALSE, если нет пользовательских атрибутов на этом поле. В противном случае возвращает код ошибки;

## <a name="remarks"></a>Примечания
 Поле может иметь несколько пользовательских атрибутов.

## <a name="see-also"></a>См. также
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
