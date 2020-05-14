---
title: IDebugCustomViewer::DisplayValue Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732449"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Этот метод называется для отображения указанного значения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Параметры
`hwnd`\
(в) Родительское окно

`dwID`\
(в) Идентификатор для пользовательских зрителей, которые поддерживают более одного типа.

`pHostServices`\
[in] Зарезервировано. Всегда установлен на нуле.

`pDebugProperty`\
(в) Интерфейс, который может быть использован для получения значения, которое будет отображаться.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Дисплей является "модальным" в том, что этот метод создаст необходимое окно, отобразит значение, будет ждать ввода и закроет окно, прежде чем вернуться к вызывающему абоненту. Это означает, что метод должен обрабатывать все аспекты отображения стоимости свойства, от создания окна для вывода до ожидания пользовательского ввода до уничтожения окна.

 Для поддержки изменения значения на данном объекте [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) можно использовать метод [SetValueAsStringWithError,](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) если значение может быть выражено как строка. В противном случае необходимо создать пользовательский интерфейс, эксклюзивный `DisplayValue` для оценщика выражения, `IDebugProperty3` реализующего этот метод, на том же объекте, который реализует интерфейс. Этот пользовательский интерфейс будет поставлять методы для изменения данных произвольного размера или сложности.

## <a name="see-also"></a>См. также
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
