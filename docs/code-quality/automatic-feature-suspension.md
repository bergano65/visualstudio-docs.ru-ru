---
title: "Приостановка работы функции автоматического | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: multiple
ms.openlocfilehash: 0bb8155f2ec1ed6815ac37f1124dfbf57cf838b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-feature-suspension"></a>Функцию автоматического приостановки
Если доступной системной памяти падает до 200 МБ или меньше, Visual Studio отображает следующее сообщение в редакторе кода.  
  
 ![Текст предупреждения, приостановка полный анализ решения](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Когда Visual Studio обнаруживает нехватки памяти, автоматически приостанавливает некоторых дополнительных функций, призванных помочь остается стабильной. Когда расширенного появится возможность приостановки предупреждение, Visual Studio будет продолжать работать, как раньше, но немного понизить его производительность.  
  
 В условиях нехватки памяти происходит следующее.  
  
-   Полный анализ решения для Visual C# и Visual Basic отключен.  
  
-   [Сборка мусора](/dotnet/standard/garbage-collection/index) режим малой задержкой (GC) для Visual C# и Visual Basic отключены.  
  
-   Visual Studio кэшей будут сброшены.  
  
## <a name="improve-visual-studio-performance"></a>Повышения производительности Visual Studio  
 Советы и рекомендации по улучшению производительности Visual Studio при работе с большими решениями или условия нехватки памяти, в разделе [вопросы производительности для больших решений](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Полный анализ решения приостановлено  
 По умолчанию полный анализ решения включена для Visual Basic и отключена для Visual C#. Однако в условиях нехватки памяти, полный анализ решения автоматически отключается для Visual Basic и Visual C#, независимо от параметров в диалоговом окне параметров. Тем не менее, можно повторно включить полный анализ решения, выбрав **повторно включить** кнопку сведений панели появлением, выбрав **включить полный анализ решения** флажок в диалоговом окне Параметры или перезапустите Visual Studio. Диалоговое окно параметров всегда показывает текущее полное решение параметры анализа. Дополнительные сведения см. в разделе [как: Включение и отключение анализа всего решения](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>Сборка Мусора малой задержкой отключена  
 Чтобы снова включить режим сборки Мусора низкой задержкой, перезапустите Visual Studio.  По умолчанию Visual Studio включает режим сборки Мусора небольшая задержка при вводе убедитесь, что текст не блокируют операции сборки Мусора. Тем не менее если нехватки памяти приводит к Visual Studio для отображения предупреждения автоматического приостановки, режим сборки Мусора низкой задержкой отключен для данного сеанса. Перезапустите Visual Studio будет включить поведение по умолчанию глобального Каталога. Дополнительные сведения см. в разделе [GCLatencyMode перечисления](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Visual Studio кэшей, в записаны на диск  
 Все кэши Visual Studio очищаются немедленно, но начнет повторно заполнить, если продолжить текущий сеанс разработки или перезапустите Visual Studio. Кэши сброшены включают кэши для следующих компонентов.  
  
-   Поиск всех ссылок  
  
-   Функция "Перейти к"  
  
-   Добавление директивы Using  
  
 Кроме того кэш, используемый для внутренних операций Visual Studio, также будут удалены.  
  
> [!NOTE]
>  Функцию автоматического приостановки предупреждение только один раз на основе каждого решения не на основе сеансов. Это означает, что, если переход от Visual Basic, Visual C# (или наоборот) и запуска в другое состояние нехватки памяти, можно возможно получить еще одно предупреждение приостановки функции автоматического.  
  
## <a name="see-also"></a>См. также  
 [Как: Включение и отключение полный анализ решения](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Основы сборки мусора](/dotnet/standard/garbage-collection/fundamentals)   
 [Вопросы производительности для больших решений](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)