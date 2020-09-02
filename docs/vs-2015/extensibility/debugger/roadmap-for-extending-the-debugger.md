---
title: Стратегия расширения отладчика | Документация Майкрософт
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
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695955"
---
# <a name="roadmap-for-extending-the-debugger"></a>Схема для расширения отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Эта документация содержит руководство и справочные сведения по расширению [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] отладчика с помощью [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Документация по отладке включает примеры, исчерпывающие ссылки и несколько репрезентативных сценариев, демонстрирующих типичные способы настройки отладчика.  
  
 Компилятор и его выходные данные определяют, что необходимо сделать для реализации отладки в вашем продукте. Если ваш компилятор:  
  
- Предназначен для встроенной операционной системы Windows и записывает. PDB-файл позволяет отлаживать программы с помощью машинного модуля отладки кода (DE), интегрированного в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Нет необходимости реализовывать средство оценки «DE» или «вычислителя выражений». Средство оценки выражений написано для синтаксиса языка программирования C++.  
  
- Создает выходные данные промежуточного языка MSIL, можно выполнять отладку программ с помощью модуля отладки управляемого кода DE, который также интегрирован в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Поэтому требуется только реализовать средство оценки выражений. Для вас предоставляется пример средства оценки выражений. Дополнительные сведения см. в следующих разделах:  
  
     [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Запись вычислителя выражений среды CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Предназначен для собственной операционной системы или какой-либо другой среды выполнения, необходимо написать собственный DE. Предоставляется учебник, в котором создается простой протокол DE-using ATL COM. Дополнительные сведения см. в следующих разделах:  
  
     [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Учебник. Создание модуля отладки с помощью ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>См. также:  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
