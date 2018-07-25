---
title: Модульное тестирование в Node.js
description: Visual Studio поддерживает код JavaScript для модульного тестирования с помощью инструментов Node.js для Visual Studio
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bc2a839583f62f3efab18fdb55274ec559d5e6cf
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924794"
---
# <a name="unit-testing-in-nodejs"></a>Модульное тестирование в Node.js

Инструменты Node.js для Visual Studio позволяют писать и выполнять модульные тесты с помощью самых популярных платформ JavaScript без необходимости переключаться на командную строку.

Поддерживаемые платформы:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Export Runner (это специальная платформа для инструментов Node.js для Visual Studio)

> [!WARNING]
> В связи с проблемой на платформе Tape в настоящее время невозможно выполнять тестирование на этой платформе. После объединения с [запросом на вытягивание 361](https://github.com/substack/tape/pull/361) проблема будет решена.

Если ваша любимая платформа не поддерживается, сведения о расширении поддержки см. в разделе [Расширение поддержки платформ для модульного тестирования](#addingFramework). 

## <a name="write-unit-tests"></a>Написание модульных тестов

Прежде чем добавлять модульные тесты в проект, убедитесь, что выбранная платформа локально установлена в проекте. Это легко сделать в [окне установки пакета npm](npm-package-management.md#npmInstallWindow).

Чтобы добавлять в проект модульные тесты, рекомендуется создать в проекте папку *tests* и настроить ее как тестовый корень в свойствах проекта. Также необходимо выбрать желаемую платформу тестирования.

![Выбор тестового корня и платформы тестирования](../javascript/media/unit-test-project-properties.png)

Вы можете добавлять в проект простые пустые тесты в диалоговом окне **Добавить новый элемент**. В одном проекте поддерживаются JavaScript и TypeScript.

![Добавление нового модульного теста](../javascript/media/unit-test-add-new-item.png)

Для модульного теста Mocha используйте следующий код:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Если вы не задали параметры модульного теста в свойствах проекта, необходимо убедиться, что для свойства **Платформа тестирования** в окне **Свойства** будет установлена верная платформа тестирования для файлов модульных тестов. Это выполняется автоматически шаблонами файлов модульного теста.

![Тестовая платформа](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Параметры модульного теста имеют приоритет над параметрами отдельных файлов.

После открытия обозревателя тестов (выберите **Тест** > **Windows** > **Обозреватель тестов**) Visual Studio обнаруживает и отображает тесты. Если тесты не отображаются изначально, перестройте проект, чтобы обновить список.

![Обозреватель тестов](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Не используйте параметр `outdir` или `outfile` в *tsconfig.json*, так как обозреватель тестов не сможет найти модульные тесты в файлах TypeScript.

## <a name="run-tests"></a>Выполнить тесты

Вы можете выполнять тесты в Visual Studio 2017 или из командной строки.

### <a name="run-tests-in-visual-studio-2017"></a>Выполнение тестов в Visual Studio 2017

Чтобы выполнить тест, нажмите на ссылку **Выполнить все** в обозревателе тестов. Или выберите один или несколько тестов или групп, щелкните правой кнопкой мыши и выберите **Выполнить выбранные тесты** из контекстного меню. Тесты выполняются в фоновом режиме, и обозреватель тестов автоматически обновится, отображая результаты. Кроме того, вы можете отладить выбранные тесты, нажав **Отладить выбранные тесты**.

> [!Warning]
> Отладка модульных тестов с помощью Node 8+ в настоящее время подходит только для тестовых файлов JavaScript. Тестовые файлы TypeScript не смогут достичь точки останова. В качестве обходного решения используйте ключевое слово `debugger`.

> [!NOTE]
> В настоящее время мы не поддерживаем тесты профилирования или объем протестированного кода.

### <a name="run-tests-from-the-command-line"></a>Запуск тестов из командной строки

Вы можете выполнять тесты из [командной строки разработчика](/dotnet/framework/tools/developer-command-prompt-for-vs) для Visual Studio 2017, используя следующую команду:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Выходные данные этой команды выглядят примерно следующим образом:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Если отобразится сообщение об ошибке, указывающее, что невозможно найти *vstest.console.exe*, убедитесь, что открыли командную строку разработчика, а не обычную командную строку. 

## <a name="addingFramework"></a>Расширение поддержки платформ модульного тестирования

Вы можете добавить поддержку дополнительных платформ тестирования, реализовав логику обнаружения и выполнения с помощью JavaScript. Для этого добавьте папку с именем платформы тестирования в раздел:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Эта папка должна содержать файл JavaScript с тем же именем, который экспортирует следующие две функции:

* `find_tests`
* `run_tests`

Хороший пример реализаций `find_tests` и `run_tests` см. в реализации платформы модульного тестирования Mocha в:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Обнаружение доступных тестовых платформ выполняется при запуске Visual Studio. Если платформа добавляется во время выполнения Visual Studio, перезапустите Visual Studio для обнаружения платформы. Но вам не нужно перезапускать платформу, если вы вносите изменения в реализацию.