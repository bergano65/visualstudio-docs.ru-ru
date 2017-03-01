---
title: "Схема для расширения отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>Схема для расширения отладчика
Эта документация содержит руководства и справочную информацию для расширения [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] отладчика с [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Отладка Документация включает примеры, полный справочник и несколько репрезентативных сценариев, демонстрирующие типичные способы настройки отладчика.  
  
 Компилятор и ее результаты выяснить, как для выполнения отладки вашего продукта. Если компилятор:  
  
-   Предназначен для собственного операционной системы Windows и записывает. PDB-файл, можно отлаживать программы с ядром отладки машинного кода (DE), который интегрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Необходимо реализовать DE или выражение оценки. Средство оценки выражений пишется для синтаксиса языка программирования C++.  
  
-   Создает выход промежуточному языку (MSIL), можно отлаживать программы с ядром отладки управляемого кода DE, который также интегрируется в Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Таким образом требуется реализовать только средство оценки выражений. Вычислитель выражений образец предоставляется автоматически. Дополнительные сведения см. в следующих разделах:  
  
     [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Контекст вычисления выражения](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Запись общих вычислитель выражений языка среды выполнения](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Целевые объекты в собственных операционная система или некоторые другие среды выполнения, необходимо написать собственный DE. В этом учебнике создается простой DE с использованием ATL COM предоставляется. Дополнительные сведения см. в следующих разделах:  
  
     [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Учебник: Создание модуля отладки с помощью ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
