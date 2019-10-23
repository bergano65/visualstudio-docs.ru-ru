---
title: Средства тестирования
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b68793e512cdb367375cc9f27d61ae5a85e4f078
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653269"
---
# <a name="testing-tools-in-visual-studio"></a>Средства тестирования Visual Studio

Средства тестирования Visual Studio могут помочь вам и вашей команде в разработке и поддержке высоких стандартов качества кода.

> [!NOTE]
> Модульное тестирование доступно во всех выпусках Visual Studio. Другие средства тестирования, такие как Live Unit Testing, IntelliTest и закодированные тесты пользовательского интерфейса, доступны только в выпуске Visual Studio Enterprise. Дополнительные сведения о выпусках см. в статье [Сравнение интегрированных сред разработки Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Обозреватель тестов

Окно **Обозреватель тестов** помогает разработчикам создавать и запускать модульные тесты, а также управлять ими. Можно использовать платформу для выполнения модульных тестов Microsoft или одну из нескольких сторонних платформ, в том числе платформы с открытым исходным кодом.

::: moniker range="vs-2017"
![Обозреватель тестов Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Обозреватель тестов Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Приступая к работе с модульным тестированием](unit-test-your-code.md)
* [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md)
* [Вопросы и ответы по обозревателю тестов](test-explorer-faq.md)
* [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md)

Visual Studio является расширяемой системой и позволяет использовать сторонние адаптеры модульного тестирования, такие как NUnit и xUnit.net. Кроме того, функция клонов кода обеспечивает высокое качество программного обеспечения, помогая определить блоки семантически сходного кода, которые являются кандидатами для совместного исправления ошибок или рефакторинга.

![Интеграция тестов сторонних разработчиков](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

Функция [Live Unit Testing](../test/live-unit-testing.md) автоматически выполняет модульные тесты в фоновом режиме и графически отображает объем протестированного кода и результаты тестирования в редакторе кода Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest автоматически создает модульные тесты и тестовые данные для управляемого кода. IntelliTest улучшает покрытие и значительно сокращает усилия, необходимые для создания и обслуживания модульных тестов для нового и существующего кода.

![IntelliTest в действии](media/devtest-intellitest.png)

* [Создание модульных тестов для кода с помощью IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — один тест на любой случай](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Справочное руководство по IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Покрытие кода

[Объем протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) позволяет определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты. Для обеспечения эффективной защиты от ошибок тесты должны выполнять ("покрывать") большую часть кода.

Анализ объема протестированного кода может применяться и к управляемому, и к неуправляемому (машинному) коду.

Покрытие кода возможно при выполнении методов тестов с помощью обозревателя тестов. В таблице результатов отображается процент кода, который был выполнен в каждой сборке, классе и методе. Кроме того, редактор исходного кода показывает, какой код был протестирован.

* [Использование параметра объема протестированного кода для определения объема протестированного кода](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Настройка анализа объема протестированного кода](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) помогает изолировать тестируемый код, заменяя другие части приложения заглушками или оболочками.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium

Закодированные тесты пользовательского интерфейса позволяют создать полностью автоматические тесты для проверки функциональности и поведения пользовательского интерфейса приложения. Они автоматизируют тестирование пользовательского интерфейса в разных технологиях, включая приложения универсальной платформы Windows на основе XAML, приложения браузера и приложения SharePoint.

Если вам нужны лучшие в своем роде закодированные тесты пользовательского интерфейса или универсальные тесты на основе браузера с использованием Selenium, Visual Studio предоставляет все необходимые для этого инструменты.

![Тестирование пользовательского интерфейса с помощью закодированных тестов](media/devtest-codeduitest.png)

* [Использование автоматизации пользовательского интерфейса для тестирования кода](use-ui-automation-to-test-your-code.md)
* [Руководство по созданию, изменению и обслуживанию закодированного теста пользовательского интерфейса](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Тестирование приложений UWP с помощью закодированных тестов пользовательского интерфейса](test-uwp-app-with-coded-ui-test.md)
* [Введение в использование закодированных тестов пользовательского интерфейса с помощью Visual Studio Enterprise (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="load-testing"></a>Нагрузочное тестирование

[Нагрузочное тестирование](../test/quickstart-create-a-load-test-project.md) позволяет моделировать нагрузку на серверное приложение посредством выполнения модульных тестов и веб-тестов производительности.

## <a name="related-scenarios"></a>Связанные сценарии

* [Произвольное и ручное тестирование (Azure Test Plans)](/azure/devops/test/index?view=vsts)
* [Нагрузочное тестирование (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts)
* [Непрерывное тестирование (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Средства анализа кода](../code-quality/code-analysis-for-managed-code-overview.md)
