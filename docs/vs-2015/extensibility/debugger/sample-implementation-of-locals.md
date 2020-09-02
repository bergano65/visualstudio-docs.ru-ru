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
ms.openlocfilehash: 6e943fd7ba27fe21029bab4d818803186147476e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704888"
---
# <a name="sample-implementation-of-locals"></a>Пример реализации локальных переменных
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже приведен обзор того, как Visual Studio получает локальные переменные для метода из средства оценки выражений (EE):  
  
1. Visual Studio вызывает [жетдебугпроперти](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) модуля отладки (de) для получения объекта [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , который представляет все свойства кадра стека, включая локальные переменные.  
  
2. `IDebugStackFrame2::GetDebugProperty` вызывает [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) для получения объекта, описывающего метод, в котором произошла точка останова. В параметре DE предоставляется поставщик символов ([идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md)), адрес ([идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md)) и связыватель ([идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` вызывает [жетконтаинерфиелд](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) с переданным `IDebugAddress` объектом для получения [идебугконтаинерфиелд](../../extensibility/debugger/reference/idebugcontainerfield.md) , представляющего метод, содержащий указанный адрес.  
  
4. `IDebugContainerField`Интерфейс запрашивает интерфейс [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) . Это интерфейс, предоставляющий доступ к локальным переменным метода.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` создает экземпляр класса (вызываемого `CFieldProperty` в примере), который реализует `IDebugProperty2` интерфейс для представления локальных переменных метода. `IDebugMethodField`Объект помещается в этот `CFieldProperty` объект вместе с `IDebugSymbolProvider` объектами, `IDebugAddress` и `IDebugBinder` .  
  
6. При `CFieldProperty` инициализации объекта вызывается [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) метод `IDebugMethodField` GetObject для объекта, чтобы получить структуру [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) , содержащую все сведения о самом методе.  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Возвращает `CFieldProperty` объект в виде `IDebugProperty2` объекта.  
  
8. Visual Studio вызывает [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для возвращенного `IDebugProperty2` объекта с фильтром `guidFilterLocalsPlusArgs` . Он возвращает объект [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , содержащий локальные переменные метода. Это перечисление заполняется вызовами [енумлокалс](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) и [енумаргументс](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio вызывает [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) , чтобы получить структуру [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) для каждого локального элемента. Эта структура содержит указатель на `IDebugProperty2` интерфейс для локального объекта.  
  
10. Visual Studio вызывает [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) для каждого локального объекта, чтобы получить имя, значение и тип локального компьютера. Это сведения, отображаемые в окне **локальные** .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Реализация GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Описывает реализацию [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Перечисление локальных переменных](../../extensibility/debugger/enumerating-locals.md)  
 Описывает, как модуль отладки (DE) выполняет вызов для перечисления локальных переменных или аргументов.  
  
 [Получение локальных свойств](../../extensibility/debugger/getting-local-properties.md)  
 Описывает, как DE вызывает метод, чтобы получить имя, тип и значение одной или нескольких локальных переменных.  
  
 [Получение локальных значений](../../extensibility/debugger/getting-local-values.md)  
 Обсуждается получение значения локальной службы, которая требует наличия служб объекта связывателя, заданного контекстом оценки.  
  
 [Вычисление локальных переменных](../../extensibility/debugger/evaluating-locals.md)  
 Объясняет, как оцениваются локальные переменные.  
  
## <a name="related-sections"></a>См. также  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, которые передаются, когда метод DE вызывает средство оценки выражений (EE).  
  
 [Пример Мицее](https://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Демонстрируется один подход к реализации для создания средства оценки выражений для языка Мик.  
  
## <a name="see-also"></a>См. также:  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
