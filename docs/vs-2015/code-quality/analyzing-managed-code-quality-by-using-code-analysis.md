---
title: Анализ качества управляемого кода с помощью анализа кода | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e0538c47dec2dd11b9488a80dd4f71baddc487f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558338"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Анализ качества управляемого кода с помощью метода анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Анализ качества управляемого кода с помощью метода анализа кода](https://docs.microsoft.com/visualstudio/code-quality/analyzing-managed-code-quality-by-using-code-analysis).  
  
Для обнаружения потенциальных проблем в коде, например, небезопасного доступа к данным, использования нарушений или проблем проектирования, можно использовать средства анализа кода в Visual Studio. Анализ кода работает в .NET Framework, машинный код (C и C++) и приложений баз данных. Анализ кода для управляемого кода объединяет правила в *наборов правил* , ориентированных на определенных проблем написания кода.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Общие задачи|Справочные материалы|  
|------------------|------------------------|  
|**Получите опыт практической:** ознакомиться с основами анализа кода, исправляя дефектов в простом приложении .NET Framework.|-   [Пошаговое руководство: Проверка управляемого кода на наличие дефектов](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Настройка анализа кода для проекта:** правил для управляемого кода организованы в наборы правил, которые указывают на конкретные области, такие как безопасность и разработки. Можно использовать один из Microsoft задает стандартное правило, или создать свой собственный.|-   [Общие сведения об управляемом коде анализе кода](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Подавление предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Запустить анализ кода:** можно указать анализ кода, чтобы запускаться автоматически каждый раз, построение конфигурации проекта, а также можно запустить анализ кода вручную для проекта.|-   [Практическое: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Практическое: запуск анализа кода вручную](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Анализ результатов анализа кода:** предупреждений анализа кода и ошибки, перечислены в окне анализа кода. Вы можете, предупреждение или ошибка заголовка для отображения дополнительных сведений о предупреждениях, а также отобразить и выделить строку исходного кода, запустившим правило. Вы можете выбрать идентификатор предупреждения, чтобы получить подробные сведения в библиотеку MSDN, которая содержит сведения и примеры того, как устранить проблему.|-   [Практическое: просмотр дефектов управляемого кода](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Анализ кода для предупреждений управляемого кода](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Предупреждения по идентификатору CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Анонимные методы и анализ кода](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Интеграция анализа кода с жизненный цикл вашей разработки:** политик возврата в [!INCLUDE[esprscc](../includes/esprscc-md.md)] позволяют команде разработки, чтобы убедиться в том, что весь код возврата удовлетворяют набору стандартов анализа кода. Создание рабочего элемента для нарушений правил анализа кода — простая процедура, которую можно выполнить в окне списка ошибок.|-   [Улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Практическое: синхронизация наборов правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Практическое: Создание рабочего элемента для дефекта управляемого кода](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



