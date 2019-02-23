---
title: IDebugField::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96ce3c428785bd6b817cb8ce0f97f14a87180d0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700678"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Этот метод возвращает отображаемую информацию о поле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

#### <a name="parameters"></a>Параметры
 `dwFields`

 [in] Сочетание [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) константы, которые выбирает данные для отображения. Если поле представляет символ, обычно это имени и типа символа.

 `pFieldInfo`

 [out] Возвращает сведения в предоставленном [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)