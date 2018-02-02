---
title: "Анализ качества управляемого кода с помощью анализа кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Анализ качества управляемого кода с помощью метода анализа кода
Для обнаружения потенциальных проблем в коде, например, небезопасного доступа к данным, использования нарушений или проблем проектирования, можно использовать средства анализа кода в Visual Studio. Анализ кода работает в .NET Framework, машинный код (C и C++) и приложений баз данных. Анализ кода для управляемого кода объединяет правила в *наборов правил* которые предназначены для определенных проблем написания кода.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Общие задачи|Справочные материалы|  
|------------------|------------------------|  
|**Получите опыт практической работы:** основы анализа кода, исправив дефектов в простом приложении .NET Framework.|-   [Пошаговое руководство: Анализ управляемого кода на наличие дефектов кода](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Настройка анализа кода для проекта:** правил для управляемого кода организованы в наборы правил, которые указывают на конкретные области, например, безопасности и разработки. Можно использовать один из Microsoft стандартное правило задает или создавать свои собственные.|-   [Анализ кода для управляемого кода Обзор](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Отключение предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Запуск анализа кода:** можно указать анализ кода, чтобы выполнялся автоматически каждый раз при построении конфигурации проекта, а также можно запустить анализ кода вручную для проекта.|-   [Как: Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Как: запуск анализа кода вручную](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Анализ результатов анализа кода:** ошибки и предупреждения анализа кода, перечислены в окне анализа кода. Вы можете, предупреждение или ошибка заголовка для отображения дополнительных сведений о предупреждениях, отображать и выделить строку исходного кода, запустившим правило. Можно выбрать идентификатор предупреждения для отображения подробных сведений в библиотеке MSDN, который содержит сведения и примеры для устранения проблемы.|-   [Как: просмотр дефектов управляемого кода](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Анализ кода для предупреждений управляемого кода](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Предупреждения по идентификатору CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Анонимные методы и анализ кода](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Интеграция анализа кода с ли жизненный цикл разработки:** политик возврата в [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] позволяют команде разработки, убедитесь, что все возвраты кода удовлетворяют набору стандартов анализа кода. Создание рабочего элемента для нарушение правила анализа кода — простая процедура, которую можно выполнить в окне списка ошибок.|-   [Улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Как: синхронизация наборов правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Как: Создание рабочего элемента для дефекта управляемого кода](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|