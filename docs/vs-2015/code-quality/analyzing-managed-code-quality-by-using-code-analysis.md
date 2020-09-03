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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d5f0646f26226e9895414db512681e0a7a71faa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671118"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Анализ качества управляемого кода с помощью метода анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для обнаружения потенциальных проблем в коде, например, небезопасного доступа к данным, использования нарушений или проблем проектирования, можно использовать средства анализа кода в Visual Studio. Анализ кода работает на .NET Framework, в машинном коде (C и C++) и в приложениях баз данных. Анализ кода для управляемого кода организует правила в *наборах правил* , предназначенных для конкретных проблем кодирования.

## <a name="common-tasks"></a>Общие задачи

|Общие задачи|Вспомогательное содержимое|
|------------------|------------------------|
|Практическое руководство **.** Изучите основы анализа кода, исправьте дефекты в простом .NET Framework приложении.|-   [Пошаговое руководство. анализ управляемого кода на предмет дефектов кода](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|
|**Настройка анализа кода для проекта.** Правила для управляемого кода организованы в наборы правил, предназначенные для конкретных областей, таких как безопасность и проектирование. Вы можете использовать один из стандартных наборов правил Майкрософт или создать собственный.|-   [Обзор анализа кода для управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Отключение предупреждений с помощью атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|
|**Запустить анализ кода:** Можно задать автоматический запуск анализа кода при каждом построении конфигурации проекта, а также выполнить анализ кода вручную в проекте.|-   [Как включить и отключить автоматический анализ кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Как выполнить анализ кода вручную](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|
|**Анализ результатов анализа кода:** Предупреждения и ошибки анализа кода перечислены в окне "анализ кода". Можно выбрать предупреждение или заголовок ошибки, чтобы отобразить дополнительные сведения о предупреждении, а также отобразить и выделить строку исходного кода, которая вызвала это правило. Вы можете выбрать идентификатор предупреждения для отображения подробных сведений в библиотеке MSDN, содержащей сведения и примеры решения проблемы.|-   [Руководство. Просмотр дефектов управляемого кода](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Анализ кода для предупреждений управляемого кода](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Предупреждения по CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Анонимные методы и анализ кода](../code-quality/anonymous-methods-and-code-analysis.md)|
|**Интегрируйте анализ кода с жизненным циклом разработки:** Политики возврата в [!INCLUDE[esprscc](../includes/esprscc-md.md)] позволяют командам разработчиков убедиться, что все возвраты кода соответствуют общему набору стандартов анализа кода. Создание рабочего элемента для нарушения правил анализа кода — это простая процедура, которую можно выполнить в окне Список ошибок.|-   [Улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Как синхронизировать наборы правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Как создать рабочий элемент для ошибки управляемого кода](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|
