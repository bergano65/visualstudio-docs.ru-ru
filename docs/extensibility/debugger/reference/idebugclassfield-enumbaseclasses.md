---
title: IDebugClassField::EnumBaseClasses Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734470"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Создает регистратор для базовых классов этого класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\

(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список базовых классов. Возвращает нулевую стоимость, если нет базовых классов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK, возвращает S_SH_NO_BASE_CLASSES, `ppEnum` если нет базовых классов (и параметр установлен на нулевую стоимость); в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Базовые классы объекта, перечисляемого, указаны в порядке самого непосредственного (или наиболее производного) базового класса для самого удаленного базового класса. Например, с учетом классов СЗ:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 Перечисление вернет базовые классы `Level2`в `Level1` `Root`порядке, .

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
