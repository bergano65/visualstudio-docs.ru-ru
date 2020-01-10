---
title: Модульное тестирование кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851260"
---
# <a name="unit-test-your-code"></a>Модульное тестирование кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модульные тесты позволяют разработчикам и тест-инженерам быстро искать логические ошибки в методах классов для проектов на языках [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] и [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)].

 Средства модульных тестов включают:

1. **Обозреватель тестов.** Обозреватель тестов позволяет выполнять модульные тесты и просматривать их результаты. Обозреватель тестов может использовать любые тестовые платформы, в том числе сторонние платформы, которые имеют адаптер для обозревателя.

2. **Платформа Microsoft для модульного тестирования управляемого кода.** Платформа для тестирования Microsoft для управляемого кода устанавливается с Visual Studio и предоставляет среду для тестирования кода в .NET.

3. **Платформа Microsoft для модульного тестирования на C++.** Платформа для выполнения модульных тестов Microsoft для C++ устанавливается с Visual Studio и предоставляет среду для тестирования машинного кода.

4. **Средства покрытия кода.** Можно определить объем кода продукта, который покрывают модульные тесты, при помощи одной команды в Обозревателе тестов.

5. **Платформа изоляции Microsoft Fakes.** Границы изоляции Microsoft Fakes могут создать постановочные классы и методы для рабочего кода и систем, которые создают зависимости в тестируемом коде. Путем реализации подставных делегатов для функции можно контролировать поведение и возвращаемые значения объекта зависимости.

   Кроме того, можно использовать компонент [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), чтобы изучить код .NET и создать тестовые данные и набор модульных тестов. Для каждого оператора в коде создаются входные данные теста, которые будут выполнять этот оператор. Анализ случая выполняется для каждой условной ветви в коде.

## <a name="key-tasks"></a>Ключевые задачи
 Следующие разделы помогут в понимании и создании модульных тестов.

|Задачи|Связанные темы|
|-----------|-----------------------|
|**Краткие и подробные руководства.** В следующих статьях можно изучить модульное тестирование в Visual Studio на конкретных примерах кода.|-   [Walkthrough: Creating and Running Unit Tests for Managed Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) (Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода)<br />-   [Quick Start: Test Driven Development with Test Explorer](../test/quick-start-test-driven-development-with-test-explorer.md) (Краткое руководство. Разработка на основе тестирования с использованием обозревателя тестов)<br />-   [Unit testing existing C++ applications with Test Explorer ](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) (Модульное тестирование существующих приложений C++ с использованием обозревателя тестов)<br />-   [Модульное тестирование машинного кода с использованием обозревателя тестов](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Модульное тестирование с помощью обозревателя тестов.** Узнайте, как с помощью обозревателя тестов создавать более производительные и более эффективные модульные тесты.|-   [Unit Test Basics](../test/unit-test-basics.md) (Основные сведения о модульных тестах)<br />-   [Create a unit test project](../test/create-a-unit-test-project.md) (Создание проекта модульного теста)<br />-   [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)<br />-   [Install third-party unit test frameworks](../test/install-third-party-unit-test-frameworks.md) (Установка платформ модульного тестирования сторонних поставщиков)<br />-   [Обновление модульных тестов с версии Visual Studio 2010](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Модульное тестирование управляемого кода**|-   [Writing Unit Tests for the .NET Framework with the Microsoft Unit Test Framework for Managed Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) (Написание модульных тестов для платформы .NET Framework с использованием платформы модульного тестирования Майкрософт для управляемого кода)|
|**Модульное тестирование кода на C++**|-   [Writing Unit tests for C/C++ with the Microsoft Unit Testing Framework for C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md) (Написание модульных тестов для языка C/C++ с использованием платформы модульного тестирования Майкрософт для C++)|
|**Изоляция модульных тестов**|-   [Isolating Code Under Test with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) (Изоляция тестируемого кода с помощью Microsoft Fakes)|
|**Использование покрытия кода для определения того, какая часть кода проекта проверяется с помощью модульных тестов.** Изучите возможности покрытия кода, которые предоставляют средства тестирования [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)].|-   [Using Code Coverage to Determine How Much Code is being Tested](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) (Использование покрытия кода для определения объема тестируемого кода)|
|**Анализ нагрузки и производительности с помощью нагрузочных тестов для модульных тестов.** Вы можете создать нагрузочный тест и добавить в него модульные тесты, чтобы выявить проблемы с нагрузкой и производительностью в приложении. **Примечание.** Создание и использование нагрузочных тестов доступно только в Visual Studio Enterprise.|-   [Creating and Editing Load Tests](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337) (Создание и изменение нагрузочных тестов)<br />-   [How to: Add Web Performance Tests and Unit Tests to a Load Test Scenario](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594) (Практическое руководство. Добавление веб-тестов производительности и модульных тестов в сценарий тестовой нагрузки)<br />-   [How to: Remove Web Tests and Unit Tests from a Load Test Scenario](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07) (Практическое руководство. Удаление веб-тестов и модульных тестов из сценария тестовой нагрузки)|
|**Установка и внедрение системы контроля качества.** Вы можете создать систему контроля качества, чтобы выполнять тесты перед сохранением кода, что поможет обеспечить его качество.|-   [Установка и внедрение системы контроля качества](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Расширение типа модульного теста.** Вы можете добавить в тесты функции, которые отсутствуют в платформе модульного тестирования. Например, можно добавить свойство теста, указывающее, должен ли тест выполняться в качестве обычного пользователя. Или можно расширить платформу, чтобы добавить строковые атрибуты в метод и использовать данные из этой строки внутри теста.|Пример кода, который расширяет платформу модульных тестов, вы найдете на следующем [веб-сайте корпорации Майкрософт](https://msdn.microsoft.com/vstudio/ff420671.aspx).|
|**Задание параметров тестирования.** Вы можете, например, задать место для сохранения результатов тестирования.|[Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>Связанные задачи
 [Просмотр результатов теста в Microsoft Test Manager](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Описывает результаты теста и способы работы с ними, включая просмотр, сохранение и удаление.

 [Running System Tests Using Microsoft Visual Studio](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130) (Запуск системных тестов с помощью Microsoft Visual Studio)

 Предоставляет ссылки на информацию об использовании Visual Studio в противоположность использованию [!INCLUDE[TCMext](../includes/tcmext-md.md)] для запуска автоматических тестов.

## <a name="reference"></a>Справочные сведения
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> описывает пространство имен UnitTesting, которое предоставляет атрибуты, исключения, утверждения и другие классы, поддерживающие модульное тестирование.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> описывает пространство имен UnitTesting. Web, которое расширяет пространство имен UnitTesting, предоставляя поддержку модульных тестов для [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] и веб-служб.

## <a name="external-resources"></a>Внешние ресурсы

### <a name="videos"></a>Видеоролики
 [Канал 9. Модульное тестирование приложений для Магазина Windows, построенных с помощью XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Форумы
 [Модульное тестирование Visual Studio](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Руководство
 [Тестирование непрерывной доставки с Visual Studio 2012 — глава 2. Модульное тестирование. Внутреннее тестирование](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Справочные сведения
 [Content Index for Unit Tests](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx) (Индекс материалов по модульным тестам)

## <a name="see-also"></a>См. также раздел
 [Улучшение тестирования качества кода](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [для приложения](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)
