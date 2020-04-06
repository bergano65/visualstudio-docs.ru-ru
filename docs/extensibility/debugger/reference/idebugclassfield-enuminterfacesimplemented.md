---
title: IDebugClassField::EnumInterfacesРеализовано (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734487"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Создает регистратор для интерфейсов, реализованных этим классом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список реализованных интерфейсов. Возвращает нулевую стоимость, если нет интерфейсов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE если нет интерфейсов реализованы на этом классе. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент перечисления представляет собой объект [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) описывающий интерфейс. Обратите внимание, [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] что неуправляемый код не использует интерфейсы в качестве дискретной [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] сущности, поэтому этот метод всегда возвращает нулевую ценность для неуправляемого кода.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
