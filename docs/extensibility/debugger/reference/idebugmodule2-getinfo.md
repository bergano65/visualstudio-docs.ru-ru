---
title: IDebugModule2::GetInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726961"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Получает информацию об этом модуле.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
(в) Комбинация флагов [из MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисления, которые `pInfo` определяют, какие поля должны быть заполнены.

`pInfo`\
(в, вне) [Структура MODULE_INFO,](../../../extensibility/debugger/reference/module-info.md) заполненная описанием модуля.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Структура [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) содержит название модуля, отображаемого в окне **модулей.**

## <a name="see-also"></a>См. также
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
