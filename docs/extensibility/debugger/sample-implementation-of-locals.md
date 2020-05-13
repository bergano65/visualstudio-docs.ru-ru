---
title: Пример реализации Местные жители (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713071"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации местных жителей
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Ниже приводится обзор того, как Visual Studio получает местных жителей для метода от оценщика выражения (EE):

1. Visual Studio вызывает отладку двигателя (DE) [GetDebugProperty,](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) чтобы получить объект [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) который представляет все свойства кадра стека, включая местных жителей.

2. `IDebugStackFrame2::GetDebugProperty`вызывает [GetMethodProperty,](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) чтобы получить объект, описывающий метод, в котором произошла точка разрыва. DE поставляет поставщик символов[(IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адрес ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), и связующего ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`вызывает [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с `IDebugAddress` поставляемым объектом, чтобы получить [IDebugContainerField,](../../extensibility/debugger/reference/idebugcontainerfield.md) который представляет метод, содержащий указанный адрес.

4. Интерфейс `IDebugContainerField` запрашивается для интерфейса [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Именно этот интерфейс дает доступ к местным жителям метода.

5. `IDebugExpressionEvaluator::GetMethodProperty`мгновенно класс (называемый `CFieldProperty` в образце), который `IDebugProperty2` запускает интерфейс для представления местных жителей метода. Объект `IDebugMethodField` помещается в `CFieldProperty` этот объект `IDebugSymbolProvider` `IDebugAddress`вместе `IDebugBinder` с, и объекты.

6. Когда `CFieldProperty` объект инициализирован, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) вызывается на `IDebugMethodField` объект, чтобы получить [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) структуру, которая содержит всю отображаемую информацию о самом методе.

7. `IDebugExpressionEvaluator::GetMethodProperty`возвращает `CFieldProperty` объект в `IDebugProperty2` качестве объекта.

8. Visual Studio вызывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) на возвращенный `IDebugProperty2` объект с помощью фильтра, `guidFilterLocalsPlusArgs`который возвращает объект [IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) содержащий местных жителей метода. Этот перечисление заполняется вызовами в [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio вызывает [Далее,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) чтобы получить [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуру для каждого местного жителя. Эта структура содержит указатель `IDebugProperty2` на интерфейс для локального.

10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого местного пользователя, чтобы получить имя, значение и тип локального пользователя. Эта информация отображается в окне **Местных жителей.**

## <a name="in-this-section"></a>В этом разделе
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Описывает реализацию [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Перечислить местных жителей](../../extensibility/debugger/enumerating-locals.md) Описывает, как движок отладки (DE) делает призыв перечислить локальные переменные или аргументы.

 [Получить локальные свойства](../../extensibility/debugger/getting-local-properties.md) Описывает, как DE делает звонок, чтобы получить имя, тип и значение одного или нескольких местных жителей.

 [Получить локальные значения](../../extensibility/debugger/getting-local-values.md) Обсуждается получение значения локального значения, которое требует услуг объекта связующего, данного контекстом оценки.

 [Оценить местных жителей](../../extensibility/debugger/evaluating-locals.md) Объясняет, как оцениваются местные жители.

## <a name="related-sections"></a>См. также
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Предоставляет аргументы, которые передаются, когда DE вызывает оценщика выражения (EE).

 [Образец MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Демонстрирует один подход к реализации для создания оценщика выражения для языка MyC.

## <a name="see-also"></a>См. также
- [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md)
