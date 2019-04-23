---
title: Схема для расширения отладчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59e12a90d241bf07a53cc98c91eef4cfc6d7d063
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050989"
---
# <a name="roadmap-for-extending-the-debugger"></a>Схема для расширения отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Эта документация содержит руководства и справочную информацию для расширения [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] отладчика с [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладка документации включает примеры, является полным Справочником и несколько репрезентативных сценариев, демонстрирующие типичные способы настройки отладчика.  
  
 Компилятор и его выходные данные определяют, что необходимо сделать для выполнения отладки вашего продукта. Если компилятор:  
  
- Предназначен для собственную операционную систему Windows и записывает. PDB-файл, можно отлаживать программы, с помощью обработчика отладки машинного кода (DE), интегрированной в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Необходимо реализовать средство DE или выражение для оценки. Средство оценки выражений записывается синтаксис языка программирования C++.  
  
- Создает выходной промежуточного языка MSIL, можно отлаживать программы, с помощью обработчика отладки управляемого кода DE, который также интегрируется в Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Таким образом требуется реализовать только вычислитель выражений. Средство оценки выражений образец предоставляется автоматически. Дополнительные сведения см. в следующих разделах:  
  
     [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Запись вычислителя выражений среды CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Целевые объекты защищенные авторским правом, операционная система или другой среды выполнения, необходимо написать собственный DE. Учебник, создающий простые DE, с помощью ATL COM предоставляется. Дополнительные сведения см. в следующих разделах:  
  
     [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Учебник. Создание модуля отладки с помощью ATL COM](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
