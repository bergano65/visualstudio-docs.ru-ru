---
title: Создание пользовательского кода и подключаемых модулей для нагрузочных тестов
description: Сведения о том, как с помощью API нагрузочных тестов и API веб-тестов производительности создать пользовательские подключаемые модули для тестов, расширяющих их встроенные функциональные возможности.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 040ca84d5da9019da87f0dfddc89cfc6b1aa043e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964450"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Создание пользовательского кода и подключаемых модулей для нагрузочных тестов

Пользовательский подключаемый модуль использует код, написанный пользователем и присоединенный к нагрузочному тесту или веб-тесту производительности. С помощью API нагрузочных тестов и API веб-тестов производительности можно создавать пользовательские подключаемые модули для тестов, расширяющие их встроенные функциональные возможности. В нагрузочный тест можно добавить несколько подключаемых модулей.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Задания

|Задания|Связанные разделы|
|-|-----------------------|
|**Создание пользовательского подключаемого модуля для нагрузочного теста**. С помощью API нагрузочных тестов можно создавать пользовательские подключаемые модули, расширяющие функциональные возможности тестирования нагрузочного теста.|-   [Практическое руководство. Использование API-интерфейса нагрузочного теста](../test/how-to-use-the-load-test-api.md)<br />-   [Практическое руководство. создание подключаемого модуля нагрузочных тестов](../test/how-to-create-a-load-test-plug-in.md)|
|**Создание пользовательского подключаемого модуля веб-теста производительности** С помощью API веб-тестов производительности можно создавать пользовательские подключаемые модули, расширяющие функциональные возможности тестирования веб-теста производительности, в том числе и на уровне запросов. Кроме того, можно создать тесты веб-служб.<br /><br /> Также можно создать подключаемый модуль веб-записи, позволяющий изменить веб-тест производительности после записи, но до появления этого теста в средстве просмотра результатов веб-тестов производительности.|-   [Практическое руководство. Использование интерфейса API веб-теста производительности](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Практическое руководство. Создание подключаемого модуля веб-теста производительности](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Практическое руководство. создание подключаемого модуля уровня запроса](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Практическое руководство. Создание теста веб-службы](../test/how-to-create-a-web-service-test.md)<br />-   [Практическое руководство. Создание подключаемого модуля записи](../test/how-to-create-a-recorder-plug-in.md)|
|**Добавление пользовательского интерфейса в средство просмотра результатов веб-тестов производительности**. С помощью надстроек Visual Studio можно добавить в средство просмотра результатов веб-тестов производительности дополнительные элементы пользовательского интерфейса.|-   [Практическое руководство. Создание надстройки Visual Studio для средства просмотра результатов веб-тестов производительности](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Создание пользовательского редактора кода HTTP**. Можно создать пользовательский редактор для работы с двоичными и строковыми XML-ответами HTTP, отправляемыми веб-службой.|-   [Практическое руководство. Создание пользовательского редактора текста HTTP для редактора веб-тестов производительности](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Справочник

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>См. также

- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Создание и запуск закодированного веб-теста производительности](../test/generate-and-run-a-coded-web-performance-test.md)
