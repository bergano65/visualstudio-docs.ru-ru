---
title: DEBUG_CUSTOM_VIEWER | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe17c8747d5c678c14561a918ddd9d62bd658841
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315837"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Структура, определяющая пользовательское средство просмотра или введите визуализатора.

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
dwID  
Идентификатор для различения нескольких средств просмотра или визуализаторы, реализованных в одном `GUID`.

bstrMenuName  
Текст, который будет отображаться в раскрывающемся меню.

bstrDescription  
Описание пользовательское средство просмотра или тип визуализатора (должен иметь значение null, если не используется).

guidLang  
Язык обеспечивает средство оценки выражений.

guidVendor  
Поставщик обеспечивает средство оценки выражений.

bstrMetric  
Метрики, под которой пользовательское средство просмотра или тип визуализатора `CLSID` хранится.

## <a name="remarks"></a>Примечания
Возвращает список этой структуры с помощью вызова [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) метод (и, следовательно, [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) метод).

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
