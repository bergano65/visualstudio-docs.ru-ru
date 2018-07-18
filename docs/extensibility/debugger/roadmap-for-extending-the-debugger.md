---
title: Путеводитель по расширению отладчик | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46c5a8a995644d6876457836674152eb3b3ccad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128108"
---
# <a name="roadmap-for-extending-the-debugger"></a>Путеводитель по расширению отладчика
Эта документация содержит руководства и справочную информацию для расширения [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] отладчик с [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Отладка документации содержит образцы, является полным Справочником и несколько репрезентативной сценарии, демонстрирующие типичные способы настройки отладчика.  
  
 Компилятор и результаты ее выполнения выяснить, как делать для выполнения отладки продукта. Если компилятор:  
  
-   Предназначен для собственного операционной системы Windows и записывает. PDB-файл, можно отлаживать программы с модуль отладки машинного кода (DE), который интегрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Необходимо реализовать DE или выражение оценки. Средство оценки выражений записывается синтаксис языка программирования C++.  
  
-   Создает выходные данные промежуточного языка MSIL можно отлаживать программы с модуль отладки управляемого кода DE, который также интегрируется в Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом должны реализовывать только вычислитель выражений. Средство оценки выражений образец подставляется автоматически. Дополнительные сведения см. в следующих разделах:  
  
     [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Запись вычислителя выражений среды CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Целевые объекты в собственных операционная система или некоторые другие среды выполнения, необходимо написать собственный DE. Учебник, в котором создается простой DE с использованием ATL COM предоставляется. Дополнительные сведения см. в следующих разделах:  
  
     [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Учебник: Создание модуля отладки с использованием ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)