---
title: Пример реализации локальных переменных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab81718837f6af8a230348d5e0a34f1da0a2c7bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092049"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Вот Общие сведения о том, как Visual Studio получает "Локальные" для метода от вычислитель выражений (EE):  
  
1. Visual Studio вызывает отладки ядра (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) для получения [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий все свойства кадра стека, включая локальные переменные.  
  
2. `IDebugStackFrame2::GetDebugProperty` вызовы [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) получить объект, описывающий метод, в котором произошла точка останова. DE предоставляет поставщик символов ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адреса ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) и привязку ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` вызовы [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с заданным идентификатором `IDebugAddress` объекта [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) представляет метод, содержащий указанный адрес.  
  
4. `IDebugContainerField` Запрашивается интерфейс [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) интерфейс. Это этот интерфейс, который предоставляет доступ к методу "Локальные".  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` Создает экземпляр класса (называется `CFieldProperty` в образце), реализующий `IDebugProperty2` интерфейс для представления метода "Локальные". `IDebugMethodField` Объект помещается в этом `CFieldProperty` вместе с `IDebugSymbolProvider`, `IDebugAddress` и `IDebugBinder` объектов.  
  
6. Когда `CFieldProperty` инициализации объекта [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) вызывается для `IDebugMethodField` объекта, чтобы получить [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) структуру, содержащую все отображаемые сведения о сам метод .  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Возвращает `CFieldProperty` объекта в виде `IDebugProperty2` объекта.  
  
8. Visual Studio вызывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращенного `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs`. Эта команда возвращает [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий метод "Локальные". Это перечисление заполняется при вызове [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio вызывает [Далее](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) для получения [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуры для каждого локального. Эта структура содержит указатель на `IDebugProperty2` интерфейса для локального.  
  
10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального для получения локальной переменной имя, значение и тип. Это информация, которая отображается в **"Локальные"** окна.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Описывает реализацию [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Перечисление локальных переменных](../../extensibility/debugger/enumerating-locals.md)  
 Описывает, как модуль отладки (DE) делает вызов для перечисления локальные переменные или аргументы.  
  
 [Получение локальных свойств](../../extensibility/debugger/getting-local-properties.md)  
 Описывает, каким образом DE делает вызов, чтобы получить имя, тип и значение одного или нескольких локальных переменных.  
  
 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md)  
 Обсуждение, получая значение локального, требуются службы объекта связыватель, выданный в контекст оценки.  
  
 [Вычисление локальных переменных](../../extensibility/debugger/evaluating-locals.md)  
 Объясняет, как оцениваются "Локальные".  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, передаваемые во время DE вызывает средство оценки выражений (EE).  
  
 [Пример MyCEE](http://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Демонстрирует реализацию подход к созданию вычислитель выражений для языка MyC.  
  
## <a name="see-also"></a>См. также  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
