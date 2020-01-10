---
title: Анализ качества приложения с помощью средств анализа кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4e45ade24ce792999d1f9b0f52d9c82703fc5a0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849882"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>{2&gt;Анализ качества приложений с помощью средств анализа кода&lt;2}
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе [Анализ качества управляемого](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) кода с помощью Visual Studio Code Analysis для управляемого кода предоставляются сведения об управляемых сборках, например о нарушениях правил программирования и проектирования, заданных в рекомендациях по проектированию Microsoft .NET Framework. В предупреждающих сообщениях указываются все проблемы, связанные с программированием и разработкой, и, по возможности, сведения о методах их устранения.

 [Анализ качества CC++ /кода с помощью анализа кода](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) . средство анализаC++ кода c/Code предоставляет разработчикам сведения о возможных дефектах в кодеC++ c/Source. Наиболее распространенные ошибки, обнаруживаемые этим средством: переполнение буфера, неинициализированная память, разыменование пустых указателей, а также утечка памяти и ресурсов.

 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Выберите и создайте *наборы правил* для применения к проекту.

 [Ошибки в приложении анализа кода](../code-quality/code-analysis-application-errors.md) Исправьте ошибки в функциях анализа кода.

 [Улучшение качества кода с помощью политик возврата командного проекта](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) При использовании система управления версиями Team Foundation (TFVC) можно создавать политики возврата для командных проектов, которые приводят к повышению качества кода и более эффективной разработки групп. Политики возврата — это правила, которые задаются на уровне командного проекта и применяются на компьютерах разработчиков, прежде чем будет разрешено выполнять возврат кода.

### <a name="code-analysis-for-drivers"></a>Анализ кода для драйверов
 Средства анализа кода могут помочь повысить стабильность и надежность драйвера путем систематического анализа исходного кода драйвера.

 [Анализ качества драйвера с помощью средств анализа кода](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) Анализ кода для драйверов — это средство статической проверки времени компиляции, которое обнаруживает основные ошибки кода в C и C++ программах и включает специализированный модуль, предназначенный для обнаружения ошибок в (в основном) коде драйвера режима ядра. Средство статической проверки (SDV) — это средство статической проверки, которое систематически анализирует исходный код в работающих в режиме ядра драйверах Windows. SDV определяет, правильно ли драйвер взаимодействует с ядром операционной системы Windows.

 [Анализ кода для драйверов предупреждения](https://msdn.microsoft.com/library/windows/hardware/ff550572(v=VS.85).aspx) Описание предупреждений, которые анализ кода для драйверов сообщает при обнаружении возможной ошибки в коде драйвера.

## <a name="related-tasks"></a>Связанные задачи
 [Измерение сложности и удобства поддержки управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Вставьте здесь описание.

 [Модульное тестирование кода](../test/unit-test-your-code.md) Вставьте здесь описание.
