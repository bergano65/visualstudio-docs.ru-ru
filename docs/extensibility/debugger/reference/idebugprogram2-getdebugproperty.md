---
title: IDebugПрограмма2::GetDebugНедвижимость Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722892"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Получает свойства программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Параметры
`ppProperty`\
(ваут) Возвращает объект [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) представляющий свойства программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Свойства, возвращенные этим методом, специфичны для программы. Если программе необходимо вернуть более одного свойства, то объект [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) возвращенный этим методом, представляет собой контейнер с дополнительными свойствами и вызов метода [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает список всех свойств.

 Программа может предоставить любое количество и тип дополнительных свойств, которые могут быть описаны `IDebugProperty2` через интерфейс. IDE может отображать дополнительные свойства программы через пользовательский интерфейс браузера общего свойства.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
