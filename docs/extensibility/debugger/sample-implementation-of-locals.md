---
title: "Пример реализации локальных переменных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c167c0a0f0a9dd0c14b92f27c0d9d862b5157072
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже приведен обзор как Visual Studio получает локальных метода от вычислитель выражений (Эстония):  
  
1.  Visual Studio вызывает отладки механизма (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий все свойства кадра стека, включая локальные переменные.  
  
2.  `IDebugStackFrame2::GetDebugProperty`вызовы [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения объекта, описывающая метод, в котором произошло точки останова. DE предоставляет поставщик символ ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адреса ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) и связыватель ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с предоставленным адресом `IDebugAddress` объекта [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) представляет метод, содержащий указанный адрес.  
  
4.  `IDebugContainerField` Запрашивается интерфейс [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейса. Это этот интерфейс обеспечивает доступ к локальные переменные для этого метода.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`Создает экземпляр класса (называется `CFieldProperty` в образце), реализующий `IDebugProperty2` интерфейс для представления метода локальные переменные. `IDebugMethodField` Объект помещается в этом `CFieldProperty` объекта вместе с `IDebugSymbolProvider`, `IDebugAddress` и `IDebugBinder` объектов.  
  
6.  При `CFieldProperty` инициализации объекта [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) будет вызван на `IDebugMethodField` объекта, чтобы получить [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) структуру, содержащую все отображаемые сведения о сам метод .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`Возвращает `CFieldProperty` объекта в виде `IDebugProperty2` объекта.  
  
8.  Visual Studio вызывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) в возвращенном `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs`. Возвращает [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий метод локальные переменные. Это перечисление заполняется вызовы [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio вызывает [Далее](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) для получения [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуру для каждой локальной. Эта структура содержит указатель на `IDebugProperty2` интерфейс для локальной.  
  
10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального для получения локальной переменной имя, значение и тип. Это информация, которая отображается в **локальные** окна.  
  
## <a name="in-this-section"></a>Содержание  
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Описывает реализацию [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Перечисление локальных переменных](../../extensibility/debugger/enumerating-locals.md)  
 Описывает, как модуль отладки (DE) позволяет перечисление локальных переменных и аргументов вызова.  
  
 [Получение локальных свойств](../../extensibility/debugger/getting-local-properties.md)  
 Описывает, каким образом DE вызывает, чтобы получить имя, тип и значение одного или нескольких локальных переменных.  
  
 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md)  
 Описание для получения значения локальной, требуются службы привязки объекта, задаваемый контекст оценки.  
  
 [Вычисление локальных переменных](../../extensibility/debugger/evaluating-locals.md)  
 Объясняет, как оцениваются локальные переменные.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые при DE вызывает вычислитель выражений (EE).  
  
 [Образец MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Демонстрирует один способ реализации создание вычислитель выражений для языка MyC.  
  
## <a name="see-also"></a>См. также  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)