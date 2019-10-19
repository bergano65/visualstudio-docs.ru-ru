---
title: Как настроить анализ кода для проекта управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658850"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Практическое руководство. Настройка анализа кода для проекта управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] и [!INCLUDE[vsPro](../includes/vspro-md.md)] можно выбрать *набор правил* анализа кода для применения к проекту управляемого кода. Набор правил по умолчанию — это минимальные Рекомендуемые правила Майкрософт. Можно применить другой набор правил к проекту или ко всем проектам в решении.

> [!NOTE]
> Сведения о настройке набора правил для веб-приложений ASP.NET см. [в разделе как настроить анализ кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Настройка набора правил для проекта .NET Framework

1. В **Обозреватель решений**щелкните проект.

2. В меню **анализ** выберите пункт **Настройка анализа кода для** *ProjectName*.

3. В списках **Конфигурация** и **платформа** выберите конфигурацию сборки и целевую платформу.

4. Для выполнения анализа кода при каждом построении проекта с использованием выбранной конфигурации установите флажок **Включить анализ кода при сборке (определяет константу CODE_ANALYSIS)** . Вы также можете запустить анализ кода вручную, открыв меню **анализ** и выбрав пункт **запустить анализ кода в** *имя_проекта*.

5. По умолчанию функция анализа кода выдает предупреждения, связанные с кодом, автоматически созданным внешними средствами. Чтобы просмотреть предупреждения из созданного кода, снимите флажок **подавлять результаты из созданного кода** .

    > [!NOTE]
    > Этот параметр не отключает ошибки и предупреждения из созданного кода, если ошибки и предупреждения появляются в формах и шаблонах. Вы можете просматривать и обслуживать исходный код для формы или шаблона.

6. В списке **выполнить этот набор правил** выполните одно из следующих действий.

    - Щелкните набор правил, который хотите использовать.

    - Щелкните **\<Browse... >** , чтобы указать существующий настраиваемый набор правил, отсутствующий в списке.

    - Определите настраиваемый набор правил.

         Дополнительные сведения см. в разделе [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>См. также раздел
 [Пошаговое руководство. Настройка и использование набора настраиваемых правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
