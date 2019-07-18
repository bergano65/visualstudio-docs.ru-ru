---
title: IDebugCustomViewer::DisplayValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d6ff987e12e70a9d3dd443cfafc45d2698469b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335694"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Этот метод вызывается для отображения указанного значения.

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
[in] Родительское окно

`dwID`\
[in] Идентификатор для пользовательских средств просмотра, которые поддерживают более одного типа.

`pHostServices`\
[in] Зарезервировано. Всегда задано значение null.

`pDebugProperty`\
[in] Интерфейс, который может использоваться для получения значения для отображения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Отображение «modal», в том, что этот метод будет создать необходимые период, отображения значения, ожидать входные данные и закрыть окно, все перед возвратом вызывающей стороне. Это означает, что метод должен обрабатывать все аспекты отображения значения свойства, от создания окна для вывода, чтобы ожидать ввода пользователя, чтобы уничтожение окна.

 Для поддержки, изменив значение на заданный [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) объекта, можно использовать [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) метод, если значение можно выразить в виде строки. В противном случае она необходима для создания пользовательского интерфейса — исключительно для оценки выражений, такая реализация `DisplayValue` метод — на тот же объект, реализующий `IDebugProperty3` интерфейс. Этот пользовательский интерфейс будет указать методы для изменения данных произвольного размера или сложности.

## <a name="see-also"></a>См. также
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)