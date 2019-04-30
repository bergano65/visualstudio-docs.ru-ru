---
title: IDebugPointerObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db0122ab12d74f6a4dd2885671067dcfe5f3254f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413505"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет собой указатель на объект.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления объект указателя.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейса можно получить этот интерфейс, используя [QueryInterface](/cpp/atl/queryinterface) Если `IDebugObject` представляет указатель.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Получает объект, на который указывает интерфейс.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Получает значение, на который указывает интерфейс, как ряд последовательных байтах.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Задает значение, на который указывает интерфейс из серию последовательных байтах.|

## <a name="remarks"></a>Примечания
 Вычислитель выражений использует этот интерфейс для представления указателя в дерево синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)