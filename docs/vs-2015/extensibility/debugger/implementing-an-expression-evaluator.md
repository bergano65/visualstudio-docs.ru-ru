---
title: Реализация вычислителя выражений | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b32ae1580ccba207f7d5e86fc4ac48d38fec7fbf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786838"
---
# <a name="implementing-an-expression-evaluator"></a>Реализация вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Вычисления выражения является сложным взаимодействием между модуль отладки (DE), поставщик символов (SP), объект модуля привязки и средство оценки выражений (EE), сам. Эти четыре компонента соединены с интерфейсами, реализованный в одном компоненте и использованы другим.  
  
 EE принимает выражение из DE в виде строки и анализирует и оценивает его. EE реализует следующие интерфейсы, которые могут использоваться DE:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE вызывает объект связыватель, предоставленный DE, чтобы получить это значение, символы и объектов. EE использует следующие интерфейсы, реализуемые с DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Реализует EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` предоставляет механизм для описания результат вычисления выражения, такие как локальная переменная, примитив или объект, для Visual Studio, которая затем отображает соответствующую информацию в **"Локальные"**,  **Контрольные значения**, или **Интерпретация** окна.  
  
  SP присваивается EE путем DE, когда он запрашивает сведения. SP реализует интерфейсы, которые описывают адреса и поля, такие как следующие интерфейсы, а также производных:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE использует все эти интерфейсы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Стратегия реализации вычислителя выражений](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Определяет трехшаговый процесс стратегия реализации вычислителя (EE) выражений.  
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

