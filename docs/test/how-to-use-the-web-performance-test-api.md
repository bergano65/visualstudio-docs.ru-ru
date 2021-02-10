---
title: API веб-теста производительности
description: Узнайте об API веб-теста производительности, который поддерживает закодированные веб-тесты производительности, подключаемые тесты, подключаемые модули запросов, правила извлечения и правила проверки.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f2afc1ab325fab8da6bdaba5650ae06d9cfcce14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969234"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Практическое руководство. Использование интерфейса API веб-теста производительности

Для веб-теста производительности можно написать код. API веб-теста производительности используется для создания закодированных веб-тестов производительности, подключаемых модулей веб-тестов производительности, подключаемых модулей запросов, правил извлечения и правил проверки. Классы, входящие в состав этих типов, являются основными классами данного API. Другие типы API используются для поддержки создания объектов <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> и <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Пользовательские веб-тесты производительности создаются в пространстве имен <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

API веб-теста производительности применяется также для программного создания и сохранения декларативных веб-тестов производительности. Для этого следует использовать классы <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> и <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> Для просмотра пространства имен <xref:Microsoft.VisualStudio.TestTools.WebTesting> используется обозреватель объектов. Редакторы Visual C# и Visual Basic предоставляют поддержку IntelliSense для создания кода с помощью классов из этого пространства имен.

Кроме того, имеется возможность создавать подключаемые модули для нагрузочных тестов. Дополнительные сведения см. в разделе [Практическое руководство. использовать API-интерфейса нагрузочного теста](../test/how-to-use-the-load-test-api.md) и [Как создать подключаемый модуль нагрузочных тестов](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Использование пространства имен WebTesting

1. Откройте проект веб-тестов производительности и нагрузочных тестов, содержащий веб-тест производительности.

2. Добавьте проект библиотеки классов Visual C# или Visual Basic в тестовое решение.

3. Добавьте ссылку на проект библиотеки классов в проект веб-тестов производительности и нагрузочных тестов.

4. Добавьте ссылку на библиотеку DLL Microsoft.VisualStudio.QualityTools.WebTestFramework в проект библиотеки классов.

5. В файл класса, расположенный в проекте библиотеки классов, добавьте оператор `using` для пространства имен <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Выполните построение проекта.

8. Добавьте новый подключаемый модуль веб-теста производительности с помощью редактора веб-тестов производительности:

    1. На панели инструментов выберите команду **Добавить подключаемый модуль веб-тестов**.

         Откроется диалоговое окно **Добавить подключаемый модуль веб-тестов**.

    2. В области **Выберите подключаемый модуль** выберите класс подключаемого модуля веб-теста производительности.

    3. В области **Свойства выбранного подключаемого модуля** задайте начальные значения для подключаемого модуля, которые будут использоваться во время выполнения.

        > [!NOTE]
        > С помощью подключаемых модулей можно предоставить доступ к произвольному количеству свойств; их необходимо сделать общедоступными, задаваемыми и относящимися к базовому типу, например к целочисленному, логическому или строковому. Кроме того, свойства подключаемого модуля веб-теста производительности можно изменить позже в окне свойств.

    4. Нажмите кнопку **ОК**.

9. Выполните веб-тест производительности.

     Пример реализации класса <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> см. в разделе [Практическое руководство. Создание подключаемого модуля веб-теста производительности](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Практическое руководство. Использование API-интерфейса нагрузочного теста](../test/how-to-use-the-load-test-api.md)
- [Практическое руководство. Создание подключаемого модуля веб-теста производительности](../test/how-to-create-a-web-performance-test-plug-in.md)
