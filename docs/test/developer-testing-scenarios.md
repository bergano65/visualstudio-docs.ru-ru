---
title: "Инструменты, сценарии и возможности тестирования для разработчика | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 0da910ddf48d0f270aa5e624628d0d6b937e9ae1
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Инструменты, сценарии и возможности тестирования для разработчика

Вы можете поддерживать работоспособность кода с помощью модульных тестов. Visual Studio предоставляет разработчикам обширный набор эффективных средств и методов для тестирования приложений:

**Сценарии и возможности:**

* [Предотвращение регрессий и обеспечение объема протестированного кода с помощью IntelliTest](#intellitest)
* [Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium](#ui-testing)
* [Эффективное модульное тестирование с обеспечением объема протестированного кода Visual Studio](#unit-testing)
* [Модульное тестирование на любой платформе с помощью высокопроизводительного обозревателя тестов](#test-explorer)
* [Приступая к работе с модульным тестированием](getting-started-with-unit-testing.md)

<a name="intellitest"></a>
## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Предотвращение регрессий и обеспечение объема протестированного кода с помощью IntelliTest

В наборах традиционных модульных тестов каждый тестовый случай представляет показательный сценарий использования, а утверждения воплощают связь между входными и выходными данными.  Проверки нескольких таких сценариев может быть вполне достаточно, но опытным разработчикам известно, что ошибки возникают даже в хорошо протестированном коде, когда непроверенные входные параметры вызывают неправильную реакцию.

Вы можете расширить объем протестированного кода и предотвратите регрессии с помощью IntelliTest.
IntelliTest значительно сокращает усилия, необходимые для создания и обслуживания модульных тестов для нового и существующего кода. 

![IntelliTest в действии](media/devtest-intellitest.png)

* [Знакомство с IntelliTest в Visual Studio](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest — один тест на любой случай](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx)
* [Видео по IntelliTest](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Начало работы с IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Справочное руководство по IntelliTest](intellitest-manual/index.md)

<a name="ui-testing"></a>
## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium

Вы можете протестировать пользовательский интерфейс с помощью лучших в своем роде или одобренных сообществом тестов.
Закодированные тесты пользовательского интерфейса позволяют создать полностью автоматические тесты для проверки функциональности и поведения пользовательского интерфейса приложения.
Они автоматизируют тестирование пользовательского интерфейса в разных технологиях, включая приложения универсальной платформы Windows на основе XAML, приложения браузера и приложения SharePoint.

Нужны ли вам лучшие в своем роде закодированные тесты пользовательского интерфейса либо универсальные тесты на основе браузера с использованием Selenium, Visual Studio предоставляет все необходимые для этого инструменты. 

![Тестирование пользовательского интерфейса с помощью закодированных тестов](media/devtest-codeduitest.png)

* [Использование модели автоматизации пользовательского интерфейса для тестирования кода](use-ui-automation-to-test-your-code.md)
* [Начало работы по созданию, изменению и обслуживанию закодированного теста пользовательского интерфейса](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Тестирование приложений универсальной платформы Windows с помощью закодированных тестов пользовательского интерфейса](test-windows-store-8-1-apps-with-coded-ui-tests.md)
* [Тестирование приложений Windows Phone с помощью закодированных тестов пользовательского интерфейса](test-windows-phone-8-1-apps-with-coded-ui-tests.md)
* [Тестирование приложений SharePoint с помощью закодированных тестов пользовательского интерфейса](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Введение в использование закодированных тестов пользовательского интерфейса с помощью Visual Studio Enterprise (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

<a name="unit-testing"></a>
## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Эффективное модульное тестирование с обеспечением объема протестированного кода Visual Studio

Чтобы определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты, можно воспользоваться функцией объема протестированного кода в Visual Studio. Для обеспечения эффективной защиты от ошибок тесты должны выполнять ("покрывать") большую часть кода.

Анализ покрытия кода может применяться и к управляемому (CLI), и к неуправляемому (машинному) коду.

Покрытие кода возможно при выполнении методов тестов с помощью обозревателя тестов. В таблице результатов отображается процент кода, который был выполнен в каждой сборке, классе и методе. Кроме того, редактор исходного кода показывает, какой код был протестирован.

![Тестирование с помощью Visual Studio Team Services и Team Foundation Server](media/devtest-codecoverage.png)

* [Использование покрытия кода для определения объема протестированного кода](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Настройка анализа покрытия кода](customizing-code-coverage-analysis.md)

<a name="test-explorer"></a>
## <a name="unit-testing-with-any-framework-using-the-high-performance-test-explorer"></a>Модульное тестирование на любой платформе с помощью высокопроизводительного обозревателя тестов

Обозреватель тестов помогает разработчикам создавать модульные тесты, управлять ими и применять их с максимальной выгодой.

![Обозреватель тестов Visual Studio](media/devtest-testexplorer.png)

* [Приступая к работе с модульным тестированием](unit-test-your-code.md)
* [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md)
* [Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)
* [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md)

Visual Studio является расширяемой системой и позволяет использовать сторонние адаптеры модульного тестирования, такие как NUnit и xUnit.net. Кроме того, функция клонов кода обеспечивает высокое качество программного обеспечения, помогая определить блоки семантически сходного кода, которые являются кандидатами для совместного исправления ошибок или рефакторинга.

![Интеграция тестов сторонних разработчиков](media/devtest-thirdparty.png)

## <a name="see-also"></a>См. также

* [Приступая к работе с модульным тестированием](getting-started-with-unit-testing.md)
* [Ускорение модульных тестов в Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/30/speeding-up-test-execution-in-tfs.aspx)
* [Параллельное и контекстное выполнение модульных тестов](https://blogs.msdn.microsoft.com/visualstudioalm/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
