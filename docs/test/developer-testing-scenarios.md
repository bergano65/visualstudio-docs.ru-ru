---
title: Инструменты тестирования для разработчиков
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 216cee6181122997ef8cc5937b9b1af76ba71b06
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316357"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Инструменты, сценарии и возможности тестирования для разработчика

Вы можете поддерживать работоспособность кода с помощью модульных тестов. Visual Studio предоставляет разработчикам обширный набор эффективных средств и методов для тестирования приложений.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Предотвращение регрессий и обеспечение объема протестированного кода с помощью IntelliTest

В наборах традиционных модульных тестов каждый тестовый случай представляет показательный сценарий использования, а утверждения воплощают связь между входными и выходными данными.  Проверки нескольких таких сценариев может быть вполне достаточно, но опытным разработчикам известно, что ошибки возникают даже в хорошо протестированном коде, когда непроверенные входные параметры вызывают неправильную реакцию.

Вы можете расширить объем протестированного кода и предотвратите регрессии с помощью IntelliTest. IntelliTest значительно сокращает усилия, необходимые для создания и обслуживания модульных тестов для нового и существующего кода.

![IntelliTest в действии](media/devtest-intellitest.png)

* [Знакомство с IntelliTest в Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest — один тест на любой случай](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Видео по IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Начало работы с IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Справочное руководство по IntelliTest](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium

Вы можете протестировать пользовательский интерфейс с помощью лучших в своем роде или одобренных сообществом тестов. Закодированные тесты пользовательского интерфейса позволяют создать полностью автоматические тесты для проверки функциональности и поведения пользовательского интерфейса приложения. Они автоматизируют тестирование пользовательского интерфейса в разных технологиях, включая приложения универсальной платформы Windows на основе XAML, приложения браузера и приложения SharePoint.

Если вам нужны лучшие в своем роде закодированные тесты пользовательского интерфейса или универсальные тесты на основе браузера с использованием Selenium, Visual Studio предоставляет все необходимые для этого инструменты.

![Тестирование пользовательского интерфейса с помощью закодированных тестов](media/devtest-codeduitest.png)

* [Использование автоматизации пользовательского интерфейса для тестирования кода](use-ui-automation-to-test-your-code.md)
* [Руководство по созданию, изменению и обслуживанию закодированного теста пользовательского интерфейса](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Тестирование приложений UWP с помощью закодированных тестов пользовательского интерфейса](test-uwp-app-with-coded-ui-test.md)
* [Тестирование приложений SharePoint с помощью закодированных тестов пользовательского интерфейса](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Введение в использование закодированных тестов пользовательского интерфейса с помощью Visual Studio Enterprise (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Эффективное модульное тестирование с обеспечением объема протестированного кода Visual Studio

Чтобы определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты, можно воспользоваться функцией объема протестированного кода в Visual Studio. Для обеспечения эффективной защиты от ошибок тесты должны выполнять ("покрывать") большую часть кода.

Анализ объема протестированного кода может применяться и к управляемому, и к неуправляемому (машинному) коду.

Покрытие кода возможно при выполнении методов тестов с помощью обозревателя тестов. В таблице результатов отображается процент кода, который был выполнен в каждой сборке, классе и методе. Кроме того, редактор исходного кода показывает, какой код был протестирован.

* [Использование параметра объема протестированного кода для определения объема протестированного кода](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Настройка анализа объема протестированного кода](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Обозреватель тестов

**Обозреватель тестов** помогает разработчикам создавать и запускать модульные тесты, а также управлять ими.

![Обозреватель тестов Visual Studio](media/devtest-testexplorer.png)

* [Приступая к работе с модульным тестированием](unit-test-your-code.md)
* [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md)
* [Вопросы и ответы по обозревателю тестов](test-explorer-faq.md)
* [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md)

Visual Studio является расширяемой системой и позволяет использовать сторонние адаптеры модульного тестирования, такие как NUnit и xUnit.net. Кроме того, функция клонов кода обеспечивает высокое качество программного обеспечения, помогая определить блоки семантически сходного кода, которые являются кандидатами для совместного исправления ошибок или рефакторинга.

![Интеграция тестов сторонних разработчиков](media/devtest-thirdparty.png)

## <a name="see-also"></a>См. также

* [Приступая к работе с модульным тестированием](getting-started-with-unit-testing.md)
* [Ускорение модульных тестов в Team Foundation Server](https://devblogs.microsoft.com/devops/speeding-up-unit-test-execution-in-tfs/)
* [Параллельное и контекстное выполнение модульных тестов](https://devblogs.microsoft.com/devops/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)
