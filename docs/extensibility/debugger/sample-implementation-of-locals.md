---
title: "Пример реализации локальные переменные | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], локальные переменные"
  - "вычисление выражений, локальные переменные"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Пример реализации локальные переменные
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Вот обзорные сведения о том, как Visual Studio получает локальных метода из выражений \(EE\):  
  
1.  Visual Studio вызывает отладки ядра \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий все свойства кадра стека, включая локальные переменные.  
  
2.  `IDebugStackFrame2::GetDebugProperty` вызывает [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения объекта, описывающая метод, в котором произошло точки останова. DE предоставляет поставщик символов \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\), адреса \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\) и привязку \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с полученным `IDebugAddress` объекта [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) представляет метод, содержащий указанный адрес.  
  
4.  `IDebugContainerField` Запрашивается интерфейс [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейс. Это этот интерфейс, который предоставляет доступ к локальные переменные метода.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` Создает экземпляр класса \(называется `CFieldProperty` в образце\), реализующий `IDebugProperty2` интерфейс представления локальные переменные метода.`IDebugMethodField` Объект помещается в этом `CFieldProperty` объекта вместе с `IDebugSymbolProvider`, `IDebugAddress` и `IDebugBinder` объектов.  
  
6.  Когда `CFieldProperty` инициализировать объект [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) вызывается на `IDebugMethodField` объекта, чтобы получить [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) Структура, содержащая все отображаемые сведения о сам метод.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Возвращает `CFieldProperty` объекта в виде `IDebugProperty2` объекта.  
  
8.  Visual Studio вызывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для возвращенного `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs`. Этот метод возвращает [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объекта, содержащего локальные переменные метода. Это перечисление заполняется путем вызова [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio вызывает [Далее](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) для получения [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуру для каждой локальной. Эта структура содержит указатель на `IDebugProperty2` интерфейс для локальной.  
  
10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального получить имя локальной переменной, значение и тип. Эти сведения, отображаемые в **Локальные** окна.  
  
## Содержание  
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Описывает реализацию [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Перечисление локальные переменные](../../extensibility/debugger/enumerating-locals.md)  
 Описывает, как отладчик \(DE\) позволяет перечислять локальные переменные или аргументы вызова.  
  
 [Получение локального свойства](../../extensibility/debugger/getting-local-properties.md)  
 Описывает, как DE позволяет вызов, чтобы получить имя, тип и значение одного или нескольких локальных переменных.  
  
 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md)  
 Описывает получение значения локального требуются службы объекта привязки, задаваемый контекст оценки.  
  
 [Определения значений локальных переменных](../../extensibility/debugger/evaluating-locals.md)  
 Объясняет, как оцениваются локальные переменные.  
  
## Связанные разделы  
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые при вызове DE вычислитель выражений \(EE\).  
  
 [MyCEE Sample](http://msdn.microsoft.com/ru-ru/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Демонстрирует реализацию подход к созданию вычислитель выражений для языка MyC.  
  
## См. также  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)