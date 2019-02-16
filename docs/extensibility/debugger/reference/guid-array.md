---
title: GUID_ARRAY | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3aa33d8cef230d07c9b5f7cd3bd11a538fa651a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315525"
---
# <a name="guidarray"></a>GUID_ARRAY
Описывает массив уникальных идентификаторов для доступных отладчиков.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="terms"></a>Термины
dwCount  
Число уникальных идентификаторов в массиве.

Участники  
Массив, содержащий уникальные идентификаторы.

## <a name="remarks"></a>Примечания
Эта структура возвращается [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) метод.

## <a name="requirements"></a>Требования
Заголовок: Msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
