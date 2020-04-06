---
title: IDebugMethodField::GetThis Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727164"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Получает `this` (в)`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]указатель объекта, содержащего метод.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Параметры
`ppClass`\
(ваут) Возвращает объект [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) представляющий "этот" указатель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В объектно-ориентированных языках, как правило, подразумевается указатель на текущее мгновенное значение класса. Это известно `this` как в C /C `Me` е [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]и как в .

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
