---
title: IDebugObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e89d7fcb33441aeb2a52218d8d74ac4dd98e4b3d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413772"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет объект, который создает связыватель для инкапсуляции значения символов и выражения.

## <a name="syntax"></a>Синтаксис

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Вычислитель выражений реализует этот интерфейс для представления объекта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс является базовым классом для всех объектов, которые использует средство оценки выражений в проанализированного выражения. Он возвращается вызовом [привязать](../../../extensibility/debugger/reference/idebugbinder-bind.md) метод. [QueryInterface](/cpp/atl/queryinterface) получает более специализированных интерфейсов из этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugObject`.

|Метод|Описание|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Возвращает размер объекта.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Возвращает значение объекта как ряд последовательных байтов.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Задает значение объекта из последовательных последовательность байтов.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Задает значения этого объекта ссылки.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Получает контекст памяти, представляющий адрес значения объекта.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Создает копию управляемого объекта в адресном пространстве для обработчика отладки.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Проверяет, является ли этот объект является пустой ссылкой.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Сравнивает объект данному.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Определяет, является ли этот объект только для чтения.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Определяет, является ли объект прозрачный прокси-сервер.|

## <a name="remarks"></a>Примечания
 Средство оценки выражений использует этот интерфейс в качестве базового класса для представления объектов в дерево синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)