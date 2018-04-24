---
title: Модульное тестирование в Visual Studio | Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f8b2ec475a4c9d8cf5799c6f429519704329c2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="unit-test-your-code"></a>Модульное тестирование кода

Модульные тесты позволяют разработчикам и тест-инженерам быстро искать логические ошибки в методах классов для проектов на языках C#, Visual Basic и C++.

Средства модульных тестов включают:

* **Обозреватель тестов**&mdash;Вы можете запускать модульные тесты и просматривать их результаты с помощью **обозревателя тестов**. Вы можете использовать любые тестовые платформы, в том числе сторонние платформы, которые имеют адаптер для **обозревателя тестов**.

* **Платформа модульного тестирования Майкрософт для управляемого кода**&mdash;Платформа для тестирования Майкрософт для управляемого кода устанавливается с Visual Studio и предоставляет среду для тестирования кода в .NET.

* **Платформа модульного тестирования Майкрософт для C++**&mdash;Платформа модульного тестирования Майкрософт для C++ устанавливается в составе рабочей нагрузки **Разработка классических приложений на C++**. Эта платформа обеспечивает тестирование машинного кода. Вдобавок включаются платформы Google Test, Boost.Test и CTest, а также сторонние адаптеры для дополнительных платформ тестирования. Дополнительные сведения см. в разделе [Создание модульных тестов для C/C++](../test/writing-unit-tests-for-c-cpp.md).

* **Инструменты покрытия кода**&mdash;Можно определить объем кода продукта, который покрывают модульные тесты, при помощи одной команды в обозревателе тестов.

* **Платформа изоляции Microsoft Fakes**&mdash;Границы изоляции Microsoft Fakes могут создать постановочные классы и методы для рабочего кода и систем, которые создают зависимости в тестируемом коде. Путем реализации подставных делегатов для функции можно контролировать поведение и возвращаемые значения объекта зависимости.

Кроме того, можно использовать компонент [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), чтобы изучить код .NET и создать тестовые данные и набор модульных тестов. Для каждого оператора в коде создаются входные данные теста, которые будут выполнять этот оператор. Анализ случая выполняется для каждой условной ветви в коде.

## <a name="key-tasks"></a>Ключевые задачи

Следующие разделы помогут в понимании и создании модульных тестов.

|Задачи|Связанные разделы|
|-----------|-----------------------|
|**Краткие и подробные руководства.** В следующих статьях можно изучить модульное тестирование в Visual Studio на конкретных примерах кода.|-   [Walkthrough: Creating and Running Unit Tests for Managed Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) (Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода)<br />-   [Краткое руководство. Разработка на основе тестирования с использованием обозревателя тестов](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Unit testing existing C++ applications with Test Explorer ](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) (Модульное тестирование существующих приложений C++ с использованием обозревателя тестов)|
|**Модульное тестирование с помощью обозревателя тестов.** Узнайте, как с помощью обозревателя тестов создавать более производительные и более эффективные модульные тесты.|-   [Unit Test Basics](../test/unit-test-basics.md) (Основные сведения о модульных тестах)<br />-   [Create a unit test project](../test/create-a-unit-test-project.md) (Создание проекта модульного теста)<br />-   [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)<br />-   [Install third-party unit test frameworks](../test/install-third-party-unit-test-frameworks.md) (Установка платформ модульного тестирования сторонних поставщиков)|
|**Модульное тестирование управляемого кода**|-   [Writing Unit Tests for the .NET Framework with the Microsoft Unit Test Framework for Managed Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) (Написание модульных тестов для платформы .NET Framework с использованием платформы модульного тестирования Майкрософт для управляемого кода)|
|**Модульное тестирование кода на C++**|-   [Writing Unit tests for C/C++ with the Microsoft Unit Testing Framework for C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md) (Написание модульных тестов для языка C/C++ с использованием платформы модульного тестирования Майкрософт для C++)|
|**Изоляция модульных тестов**|-   [Isolating Code Under Test with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) (Изоляция тестируемого кода с помощью Microsoft Fakes)|
|**Использование покрытия кода для определения того, какая часть кода проекта тестируется.** Изучите возможности покрытия кода, которые предоставляют средства тестирования Visual Studio.|-   [Using Code Coverage to Determine How Much Code is being Tested](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) (Использование покрытия кода для определения объема тестируемого кода)|
|**Анализ нагрузки и производительности с помощью нагрузочных тестов.** Вы можете создать нагрузочный тест и добавить в него модульные тесты, чтобы выявить проблемы с нагрузкой и производительностью в приложении.|-   [Нагрузочное тестирование (VSTS и TFS)](/vsts/load-test/)|
|**Установка системы контроля качества.** Вы можете создать систему контроля качества, чтобы выполнять тесты перед сохранением кода и обеспечить его качество.|-   [Политики возврата (VSTS)](/vsts/tfvc/add-check-policies)|
|**Задание параметров тестирования.** Вы можете, например, задать место для сохранения результатов тестирования.|[Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Справочная документация по API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> описывает пространство имен UnitTesting, предоставляющего атрибуты, исключения, утверждения и другие классы, поддерживающие модульное тестирование.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> описывает пространство имен UnitTesting.Web, расширяющего пространство имен UnitTesting за счет поддержки ASP.NET и модульных тестов веб-службы.

## <a name="see-also"></a>См. также

- [Улучшение качества кода](/visualstudio/test/improve-code-quality)
