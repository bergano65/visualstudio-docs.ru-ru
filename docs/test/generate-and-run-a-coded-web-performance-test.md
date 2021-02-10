---
title: Закодированные веб-тесты производительности
description: Сведения о том, как веб-тест производительности можно преобразовать в скрипт на основе кода, разрешающий редактирование и настройку.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 74269872992935568362a061d47f7335dbaedec8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936422"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Создание и запуск закодированного веб-теста производительности

Веб-тесты производительности записываются путем просмотра из веб-приложения. Тесты включены в нагрузочные тесты для измерения производительности веб-приложения под нагрузкой, создаваемой несколькими пользователями. Веб-тест производительности можно преобразовать в скрипт на основе кода, который можно редактировать и адаптировать, как любой другой исходный код. Например, можно добавлять циклические конструкции и конструкции ветвления.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>Создание закодированного веб-теста производительности

1. Если веб-тест производительности еще не создан, см. раздел [Запись веб-теста производительности](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2. Создайте закодированный тест.

     ![Создание закодированного веб-теста производительности](../test/media/web_test_coded_generate.png)

3. Назовите тест.

     ![Ввод имени для закодированного веб-тест производительности](../test/media/web_test_coded_generate_nametest.png)

     Новый закодированный тест откроется в редакторе кода.

     В зависимости от того, какой шаблон проекта веб-теста производительности и нагрузочного теста вы добавили в решение, код будет создан в Visual Basic или Visual C#.

     ![Новый закодированный тест открывается в редакторе кода](../test/media/web_test_coded_generate_opencodeeditor.png)

     В коде можно увидеть, что метод GetRequestEnumerator() в C# или метод Run() в Visual Basic содержит все правила проверки и веб-запрос, сделанный в тесте с измененным кодом.

4. Чтобы продемонстрировать добавление простого кода, прокрутите до конца метода и после кода последнего веб-запроса добавьте следующий код:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. Соберите решение, чтобы убедиться, что пользовательский код компилируется.

6. Запустите тест.

     ![Запуск закодированного веб-теста производительности](../test/media/web_test_coded_generate_run.png)

     А поскольку запуск выполнялся в среду...

     ![Результаты закодированного веб-теста производительности](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Вопросы и ответы

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Вопрос: Можно ли запустить несколько тестов одновременно?
**Ответ.** Да, используйте контекстное меню в **обозревателе решений**.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Вопрос: Добавлять источник данных следует до или после создания закодированного теста?
**Ответ.** Проще [добавить источник данных](../test/add-a-data-source-to-a-web-performance-test.md) до создания закодированного теста, потому что в этом случае код будет создан автоматически.

При запуске закодированного теста с источником данных возможно отображение следующего сообщения об ошибке.

**Не удалось выполнить тест \<Test Name> в агенте \<Computer Name>: Ссылка на объект не указывает на экземпляр объекта.**

Это может произойти, если для класса теста определен атрибут DataSourceAttribute без соответствующего атрибута DataBindingAttribute. Чтобы устранить эту ошибку, добавьте соответствующий атрибут DataBindingAttribute, удалите лишний атрибут или преобразуйте его в комментарий в коде.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Вопрос: Добавлять правила проверки и извлечения следует до или после создания закодированного теста?
**Ответ.** Проще добавить правила проверки и правила извлечения до создания закодированного теста; но мы рекомендуем использовать для проверки [закодированные тесты пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md).
