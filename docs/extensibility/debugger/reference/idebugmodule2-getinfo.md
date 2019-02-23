---
title: IDebugModule2::GetInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0a5ad3d7651e89c2ef864a184155e8b0a430d79
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694807"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Возвращает сведения об этом модуле.

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

#### <a name="parameters"></a>Параметры
 `dwFields`

 [in] Сочетание флагов из [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисление, указать, какие поля из `pInfo` , для заполнения.

 `pInfo`

 [in, out] Объект [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры, который заполняется описание модуля.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структура содержит имя модуля, который отображается в **модули** окна.

## <a name="see-also"></a>См. также
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)