---
title: Средства тестирования
ms.date: 03/16/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 12089bf5033ed126558fb2e859a3132aecd0cde5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972499"
---
# <a name="testing-tools-in-visual-studio"></a>Средства тестирования Visual Studio

Средства тестирования Visual Studio могут помочь вам и вашей команде в разработке и поддержке высоких стандартов качества кода.

- **Обозреватель тестов** позволяет легко интегрировать [модульные тесты](../test/unit-test-your-code.md) в вашу практику разработки. Можно использовать платформу для выполнения модульных тестов Microsoft или одну из нескольких сторонних платформ, в том числе платформы с открытым исходным кодом.

- [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) автоматически создает модульные тесты и тестовые данные для управляемого кода.

- [Объем протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) позволяет определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты.

- [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) помогает изолировать тестируемый код, заменяя другие части приложения заглушками или оболочками.

- Функция [Live Unit Testing](../test/live-unit-testing.md) автоматически выполняет модульные тесты в фоновом режиме и графически отображает объем протестированного кода и результаты тестирования в редакторе кода Visual Studio.

- С помощью [закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md) можно проверять работу пользовательского интерфейса приложения.

- [Нагрузочное тестирование](../test/quickstart-create-a-load-test-project.md) позволяет моделировать нагрузку на серверное приложение посредством выполнения модульных тестов и веб-тестов производительности.

> [!NOTE]
> Модульное тестирование доступно во всех выпусках Visual Studio. Другие средства тестирования, такие как Live Unit Testing, IntelliTest и закодированные тесты пользовательского интерфейса, доступны только в выпуске Visual Studio Enterprise. Дополнительные сведения о выпусках см. в статье [Сравнение интегрированных сред разработки Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/).

## <a name="related-scenarios"></a>Связанные сценарии

* [Произвольное и ручное тестирование (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Нагрузочное тестирование (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Непрерывное тестирование (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Средства анализа кода](../code-quality/code-analysis-for-managed-code-overview.md)
