---
title: Анализ качества управляемого кода с помощью анализа кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d8740b79b026ade7f3da19aa4a89cacd94df17d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990103"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Анализ качества управляемого кода с помощью метода анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для обнаружения потенциальных проблем в коде, например, небезопасного доступа к данным, использования нарушений или проблем проектирования, можно использовать средства анализа кода в Visual Studio. Анализ кода работает в .NET Framework, машинный код (C и C++) и приложений баз данных. Анализ кода для управляемого кода объединяет правила в *наборов правил* , ориентированных на определенных проблем написания кода.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Общие задачи|Справочные материалы|  
|------------------|------------------------|  
|**Получите практические рекомендации:** Изучите основы анализа кода, исправляя дефектов в простом приложении .NET Framework.|-   [Пошаговое руководство: Анализ управляемого кода на наличие дефектов](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Настройка анализа кода для проекта:** Правила для управляемого кода организованы в наборы правил, которые указывают на конкретные области, такие как безопасность и разработки. Можно использовать один из Microsoft задает стандартное правило, или создать свой собственный.|-   [Общие сведения об управляемом коде анализе кода](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Подавление предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Запустите анализ кода:** Можно указать анализ кода, чтобы запускаться автоматически каждый раз, построение конфигурации проекта, и можно запустить анализ кода вручную для проекта.|-   [Практическое руководство. Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Практическое руководство. Запуск анализа кода вручную](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Анализ результатов анализа кода.** Предупреждения анализа кода и ошибки, перечислены в окне анализа кода. Вы можете, предупреждение или ошибка заголовка для отображения дополнительных сведений о предупреждениях, а также отобразить и выделить строку исходного кода, запустившим правило. Вы можете выбрать идентификатор предупреждения, чтобы получить подробные сведения в библиотеку MSDN, которая содержит сведения и примеры того, как устранить проблему.|-   [Практическое руководство. Просмотр дефектов управляемого кода](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Анализ кода для предупреждений управляемого кода](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Предупреждения по идентификатору CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Анонимные методы и анализ кода](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Интеграция анализа кода с жизненный цикл вашей разработки.** Политики возврата в [!INCLUDE[esprscc](../includes/esprscc-md.md)] позволяют команде разработки, чтобы убедиться в том, что весь код возврата удовлетворяют набору стандартов анализа кода. Создание рабочего элемента для нарушений правил анализа кода — простая процедура, которую можно выполнить в окне списка ошибок.|-   [Улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Практическое руководство. Синхронизация наборов правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Практическое руководство. Создание рабочего элемента для дефекта управляемого кода](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
