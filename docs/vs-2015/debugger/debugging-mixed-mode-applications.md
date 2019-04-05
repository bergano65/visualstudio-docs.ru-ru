---
title: Отладка приложений в смешанном режиме | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 83b43b1bb5e47b4d916f18f5a59bba8c04dd21eb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994057"
---
# <a name="debugging-mixed-mode-applications"></a>Отладка приложений со смешанным режимом
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Приложением смешанного режима называется любое приложение, объединяющее машинный код (C++) с управляемым кодом (кодом на Visual Basic, Visual C# или управляемыми расширениями для C++, которые запускаются в среде CLR). Отладка приложений в смешанном режиме в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] довольно прозрачна, ее отличия от отладки обычных приложений несущественны. Однако и здесь существуют некоторые особенности.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Включение режима "Изменить и продолжить" для C++ при отладке в смешанном режиме  
  
-   Чтобы применить режим "Изменить и продолжить" для C++ в Visual Studio 2013 необходимо вернуться к прежнему ядру отладки. См. публикацию [Переключение в режим совместимости управляемого кода в Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) в блоге Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Вычисление свойств в приложениях в смешанном режиме  
 В приложениях со смешанным режимом вычисление свойств отладчиком является ресурсоемкой операцией. Поэтому такие операции отладки, как пошаговое выполнение, могут выполняться медленно. Дополнительные сведения см. в разделе [Пошаговое выполнение](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Если производительность системы во время отладки в смешанном режиме слишком низкая, можно отключить вычисление свойств в окнах отладчика.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Чтобы отключить вычисление свойств  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
2. В диалоговом окне **Параметры** откройте папку **Отладка** и выберите категорию **Общие**.  
  
3. Снимите флажок **Включить вычисление свойств и другие неявные вызовы функций**.  
  
   Поскольку машинный стек вызовов отличается от управляемого стека вызовов, отладчик не всегда может предоставить полный стек вызовов для смешанного кода. Когда машинный код вызывает управляемый код, могут возникнуть некоторые несоответствия. Дополнительные сведения см. в разделе [Смешанный код и отсутствующая информация в окне стека вызовов](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
