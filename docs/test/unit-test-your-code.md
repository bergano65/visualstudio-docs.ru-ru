---
title: "Модульное тестирование кода | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bafabb6755a5d3c8cf8f2b60b67a9dc0d7af9792
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="unit-test-your-code"></a>Модульное тестирование кода
Модульные тесты позволяют разработчикам и тест-инженерам быстро искать логические ошибки в методах классов для проектов на языках [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] и [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].  
  
 Средства модульных тестов включают:  
  
1.  **Обозреватель тестов.** Обозреватель тестов позволяет выполнять модульные тесты и просматривать их результаты. Обозреватель тестов может использовать любые тестовые платформы, в том числе сторонние платформы, которые имеют адаптер для обозревателя.  
  
2.  **Платформа Microsoft для модульного тестирования управляемого кода.** Платформа для тестирования Microsoft для управляемого кода устанавливается с Visual Studio и предоставляет среду для тестирования кода в .NET.  
  
3.  **Платформа Microsoft для модульного тестирования на C++.** Платформа для выполнения модульных тестов Microsoft для C++ устанавливается с Visual Studio и предоставляет среду для тестирования машинного кода.  Кроме того, в состав Visual Studio входят платформы Google Test, Boost.Test и CTest, а также сторонние адаптеры для дополнительных платформ тестирования. Дополнительные сведения см. в разделе [Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md). 
  
4.  **Средства покрытия кода.** Можно определить объем кода продукта, который покрывают модульные тесты, при помощи одной команды в Обозревателе тестов.  
  
5.  **Платформа изоляции Microsoft Fakes.** Границы изоляции Microsoft Fakes могут создать постановочные классы и методы для рабочего кода и систем, которые создают зависимости в тестируемом коде. Путем реализации подставных делегатов для функции можно контролировать поведение и возвращаемые значения объекта зависимости.  
  
 Кроме того, можно использовать компонент [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md), чтобы изучить код .NET и создать тестовые данные и набор модульных тестов. Для каждого оператора в коде создаются входные данные теста, которые будут выполнять этот оператор. Анализ случая выполняется для каждой условной ветви в коде.  
  
## <a name="key-tasks"></a>Ключевые задачи  
 Следующие разделы помогут в понимании и создании модульных тестов.  
  
|Задачи|Связанные разделы|  
|-----------|-----------------------|  
|**Краткие и подробные руководства.** В следующих статьях можно изучить модульное тестирование в Visual Studio на конкретных примерах кода.|-   [Walkthrough: Creating and Running Unit Tests for Managed Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) (Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода)<br />-   [Quick Start: Test Driven Development with Test Explorer](../test/quick-start-test-driven-development-with-test-explorer.md) (Краткое руководство. Разработка на основе тестирования с использованием обозревателя тестов)<br />-   [Unit testing existing C++ applications with Test Explorer ](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) (Модульное тестирование существующих приложений C++ с использованием обозревателя тестов)|  
|**Модульное тестирование с помощью обозревателя тестов.** Узнайте, как с помощью обозревателя тестов создавать более производительные и более эффективные модульные тесты.|-   [Unit Test Basics](../test/unit-test-basics.md) (Основные сведения о модульных тестах)<br />-   [Create a unit test project](../test/create-a-unit-test-project.md) (Создание проекта модульного теста)<br />-   [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)<br />-   [Install third-party unit test frameworks](../test/install-third-party-unit-test-frameworks.md) (Установка платформ модульного тестирования сторонних поставщиков)<br />-   [Обновление закодированных тестов пользовательского интерфейса с версии Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)|  
|**Модульное тестирование управляемого кода**|-   [Writing Unit Tests for the .NET Framework with the Microsoft Unit Test Framework for Managed Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md) (Написание модульных тестов для платформы .NET Framework с использованием платформы модульного тестирования Майкрософт для управляемого кода)|  
|**Модульное тестирование кода на C++**|-   [Writing Unit tests for C/C++ with the Microsoft Unit Testing Framework for C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md) (Написание модульных тестов для языка C/C++ с использованием платформы модульного тестирования Майкрософт для C++)|  
|**Изоляция модульных тестов**|-   [Isolating Code Under Test with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) (Изоляция тестируемого кода с помощью Microsoft Fakes)|  
|**Использование покрытия кода для определения того, какая часть кода проекта проверяется с помощью модульных тестов.** Изучите возможности покрытия кода, которые предоставляют средства тестирования [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)].|-   [Using Code Coverage to Determine How Much Code is being Tested](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) (Использование покрытия кода для определения объема тестируемого кода)|  
|**Анализ нагрузки и производительности с помощью нагрузочных тестов для модульных тестов.** Вы можете создать нагрузочный тест и добавить в него модульные тесты, чтобы выявить проблемы с нагрузкой и производительностью в приложении.|-   [Нагрузочное тестирование (VSTS и TFS)](/vsts/load-test/)|  
|**Установка и внедрение системы контроля качества.** Вы можете создать систему контроля качества, чтобы выполнять тесты перед сохранением кода и обеспечить его качество.|-   [Установка и внедрение системы контроля качества](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Расширение типа модульного теста.** Вы можете добавить в тесты функции, которые отсутствуют в платформе модульного тестирования. Например, можно добавить свойство теста, указывающее, должен ли тест выполняться в качестве обычного пользователя. Или можно расширить платформу, чтобы добавить строковые атрибуты в метод и использовать данные из этой строки внутри теста.|Пример кода, который расширяет платформу модульных тестов, вы найдете на следующем [веб-сайте корпорации Майкрософт](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Задание параметров тестирования.** Вы можете, например, задать место для сохранения результатов тестирования.|[Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Описание пространства имен UnitTesting, предоставляющего атрибуты, исключения, утверждения и другие классы, поддерживающие модульное тестирование.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Описание пространства имен UnitTesting.Web, расширяющего пространство имен UnitTesting за счет поддержки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и модульных тестов веб-службы.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
### <a name="videos"></a>Видеоролики  
 [Канал 9. Модульное тестирование приложений универсальной платформы Windows, построенных с помощью XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Форумы  
 [Visual Studio Unit Testing](http://go.microsoft.com/fwlink/?LinkId=224477) (Модульное тестирование в Visual Studio)  
  
### <a name="guidance"></a>Руководство  
 [Тестирование непрерывной доставки с Visual Studio 2012 — глава 2. Модульное тестирование. Внутреннее тестирование](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### <a name="reference"></a>Ссылка  
 [Content Index for Unit Tests](http://go.microsoft.com/fwlink/?LinkID=254719) (Индекс материалов по модульным тестам)  
  
## <a name="see-also"></a>См. также

[Улучшение качества кода](/visualstudio/test/improve-code-quality)
