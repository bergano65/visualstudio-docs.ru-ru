---
title: Отладка приложений в смешанном режиме | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4170a63597611bb190a6b3cf365b6dbced1bc9ae
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389394"
---
# <a name="debugging-mixed-mode-applications"></a>Отладка приложений со смешанным режимом
Приложением смешанного режима называется любое приложение, объединяющее машинный код (C++) с управляемым кодом (кодом на Visual Basic, Visual C# или управляемыми расширениями для C++, которые запускаются в среде CLR). Отладка приложений в смешанном режиме в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] довольно прозрачна, ее отличия от отладки обычных приложений несущественны. Однако и здесь существуют некоторые особенности.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Включение режима "Изменить и продолжить" для C++ при отладке в смешанном режиме

Чтобы изменить и продолжить для C++, см. в разделе [как включить и отключить, изменить и продолжить](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Чтобы применить режим "Изменить и продолжить" для C++ в Visual Studio 2013 необходимо вернуться к прежнему ядру отладки. См. публикацию [Переключение в режим совместимости управляемого кода в Visual Studio 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/) в блоге Microsoft Application Lifecycle Management.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Вычисление свойств в приложениях в смешанном режиме
 В приложениях со смешанным режимом вычисление свойств отладчиком является ресурсоемкой операцией. Поэтому такие операции отладки, как пошаговое выполнение, могут выполняться медленно. Дополнительные сведения см. в разделе [Пошаговое выполнение](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Если производительность системы во время отладки в смешанном режиме слишком низкая, можно отключить вычисление свойств в окнах отладчика.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Чтобы отключить вычисление свойств

1. В меню **Сервис** выберите пункт **Параметры**.

2. В диалоговом окне **Параметры** откройте папку **Отладка** и выберите категорию **Общие**.

3. Снимите флажок **Включить вычисление свойств и другие неявные вызовы функций**.

   Поскольку машинный стек вызовов отличается от управляемого стека вызовов, отладчик не всегда может предоставить полный стек вызовов для смешанного кода. Когда машинный код вызывает управляемый код, могут возникнуть некоторые несоответствия. Дополнительные сведения см. в разделе [Смешанный код и отсутствующая информация в окне стека вызовов](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>См. также

- [Отладка управляемого кода](../debugger/debugging-managed-code.md)