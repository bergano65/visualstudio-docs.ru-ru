---
title: DEBUG_CUSTOM_VIEWER Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737542"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Структура, идентифицирует пользовательского просмотра или ввизуализатор.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Участники
`dwID`\
Идентификатор для дифференцирования `GUID`нескольких зрителей или визуализаторов, реализованных одним.

`bstrMenuName`\
Текст, который появится в меню выпадения.

`bstrDescription`\
Описание пользовательского просмотра или ввизуализатора (должно быть нулевая стоимость, если не используется).

`guidLang`\
Язык оценщика выражения.

`guidVendor`\
Поставщик оценщика выражения.

`bstrMetric`\
Метрика, под которой хранится `CLSID` пользовательский зритель или визуализатор типа.

## <a name="remarks"></a>Примечания
Список этой структуры возвращается путем вызова метода [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (и, соответственно, метод [GetCustomViewerList).](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
