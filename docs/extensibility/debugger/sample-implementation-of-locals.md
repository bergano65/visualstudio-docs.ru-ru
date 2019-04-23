---
title: Пример реализации локальных переменных | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17de5858870afe3064f57cb51ec8b713bb65ddf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047649"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ниже приведен обзор как Visual Studio получает "Локальные" для метода из вычислитель выражений (EE).

1. Visual Studio вызывает отладки ядра (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий все свойства кадра стека, включая локальные переменные.

2. `IDebugStackFrame2::GetDebugProperty` вызовы [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) получить объект, описывающий метод, в течение которого произошло точки останова. DE предоставляет поставщик символов ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адреса ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) и привязку ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с заданным идентификатором `IDebugAddress` объекта [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , представляющий метод, содержащий указанный адрес.

4. `IDebugContainerField` Запрашивается интерфейс [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейс. Это этот интерфейс, который предоставляет доступ к методу "Локальные".

5. `IDebugExpressionEvaluator::GetMethodProperty` Создает экземпляр класса (называется `CFieldProperty` в образце), которое будет выполняться `IDebugProperty2` интерфейс для представления метода "Локальные". `IDebugMethodField` Объект помещается в этом `CFieldProperty` вместе с `IDebugSymbolProvider`, `IDebugAddress`, и `IDebugBinder` объектов.

6. При `CFieldProperty` инициализации объекта [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) вызывается для `IDebugMethodField` объекта [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) структуру, содержащую все отображаемые сведения о сам метод.

7. `IDebugExpressionEvaluator::GetMethodProperty` Возвращает `CFieldProperty` объекта в виде `IDebugProperty2` объекта.

8. Visual Studio вызывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращенного `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs`, который возвращает [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий метод "Локальные". Это перечисление заполняется при вызове [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio вызывает [Далее](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) для получения [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуры для каждого локального. Эта структура содержит указатель на `IDebugProperty2` интерфейса для локального.

10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального для получения локальной переменной имя, значение и тип. Эта информация отображается в **"Локальные"** окна.

## <a name="in-this-section"></a>Содержание раздела
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) описывает реализацию [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Перечислять локальные переменные](../../extensibility/debugger/enumerating-locals.md) описывает, как модуль отладки (DE) делает вызов для перечисления локальные переменные или аргументы.

 [Получение локальных свойств](../../extensibility/debugger/getting-local-properties.md) описывает, каким образом DE делает вызов, чтобы получить имя, тип и значение одного или нескольких локальных переменных.

 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md) описание, получение локальной, требуются службы объекта связыватель, выданный в контекст оценки.

 [Оценить локальные](../../extensibility/debugger/evaluating-locals.md) объясняет, как оцениваются "Локальные".

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) предоставляет аргументы, передаваемые во время DE вызывает средство оценки выражений (EE).

 [Пример MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) демонстрирует создание вычислитель выражений для языка MyC один из способов реализации.

## <a name="see-also"></a>См. также
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)