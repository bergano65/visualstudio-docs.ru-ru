---
title: Параметры командной строки для VSTest.Console.exe
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8264aebcbced16f95c177d255e226cfffdbee0ce
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869598"
---
# <a name="vstestconsoleexe-command-line-options"></a>Параметры командной строки для VSTest.Console.exe

*VSTest.Console.exe* — это программа командной строки для выполнения тестов. В командной строке можно указывать несколько параметров в произвольном порядке. Эти параметры перечислены в таблице [Общие параметры командной строки](#general-command-line-options) ниже.

> [!NOTE]
> Адаптер MSTest в Visual Studio также способен работать в прежнем режиме (эквивалентном выполнению тестов с помощью *mstest.exe*) в целях совместимости. В прежнем режиме невозможно использовать новые возможности компонента TestCaseFilter. Адаптер может переключиться в прежний режим, если задан *TESTSETTINGS-файл*, параметр **forcelegacymode** в *RUNSETTINGS-файле* установлен в значение **true**, или с помощью атрибутов, таких как **HostType**.
>
> Для выполнения автоматических тестов на компьютере с архитектурой ARM необходимо использовать *VSTest.Console.exe*.

Откройте [Командную строку разработчика](/dotnet/framework/tools/developer-command-prompt-for-vs), чтобы использовать программу командной строки. Это средство можно также найти в папке *%Program Files(x86)%\Microsoft Visual Studio\\<версия\>\\<выпуск\>\common7\ide\CommonExtensions\\<Платформа | Microsoft>* .

## <a name="general-command-line-options"></a>Общие параметры командной строки

В следующей таблице перечислены все параметры *VSTest.Console.exe* и приведено их краткое описание. Аналогичные данные можно получить, введя `VSTest.Console/?` в командной строке.

| Параметр | Описание |
|---|---|
|**[*тестовых*]**|Запускает тесты из указанных файлов. Для разделения имен тестовых файлов используйте пробелы.<br />Примеры: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*имя файла*]**|Запуск тестов с дополнительными параметрами, например со сборщиками данных. Дополнительные сведения см. в разделе [Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).<br />Пример: `/Settings:local.runsettings`|
|**/Tests:[*имя теста*]**|Выполняйте тесты с именами, которые соответствуют заданным значениям. Для предоставления нескольких значений разделите их запятыми.<br />Пример: `/Tests:TestMethod1,testMethod2`<br />Параметр командной строки **/Tests** нельзя использовать с параметром командной строки **/TestCaseFilter**.|
|**/Parallel**|Указывает, что тесты должны выполняться параллельно. По умолчанию могут использоваться все доступные на компьютере ядра. Число ядер для использования можно настроить с помощью файла параметров.|
|**/Enablecodecoverage**|Включение адаптера диагностических данных CodeCoverage в тестовом запуске.<br />Параметры по умолчанию используются, если другие параметры не заданы с использованием файла параметров.|
|**/InIsolation**|Запуск тестов в изолированном процессе.<br />Эта изоляция существенно снижает вероятность остановки процесса *vstest.console.exe* при возникновении ошибки в тестах, однако тесты могут выполняться медленнее.|
|**/UseVsixExtensions**|Процесс *vstest.console.exe* будет использовать или пропускать установленные расширения VSIX (если они имеются) при запуске тестов.<br />Этот параметр использовать не рекомендуется. Уже в следующем основном выпуске Visual Studio этот параметр может быть удален. Переходите на использование расширений, доступных в виде пакета NuGet.<br />Пример: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*путь*]**|Процесс *vstest.console.exe* в тестовом запуске будет использовать адаптеры пользовательских тестов по указанному пути (если они там есть).<br />Пример: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*тип платформы*]**|Архитектура целевой платформы, которая должна использоваться для выполнения тестов.<br />Допустимые значения — x86, x64 и ARM.|
|**/Framework: [*версия платформы*]**|Целевая версия .NET, которую следует использовать для выполнения тестов.<br />Примеры значений: `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10`, `.NETCoreApp,Version=v1.1`.<br />TargetFrameworkAttribute используется для автоматического обнаружения этого параметра в сборке, его значение по умолчанию `Framework40`, если отсутствует атрибут. Этот параметр необходимо указывать явно, если из сборок .NET Core.удален [TargetFrameworkAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.versioning.targetframeworkattribute).<br />Если целевая версия платформы задана как **Framework35**, тесты выполняются в "режиме совместимости" среды CLR 4.0.<br />Пример: `/Framework:framework40`|
|**/TestCaseFilter:[*выражение*]**|Запуск тестов, соответствующих заданному выражению.<br /><Выражение\> формата <свойство\>=<значение\>[\|<Выражение\>].<br />Пример: `/TestCaseFilter:"Priority=1"`<br />Пример: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Параметр командной строки **/TestCaseFilter** нельзя использовать с параметром командной строки **/Tests**. <br />Сведения о создании и использовании выражений см. в разделе [Фильтр TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Отображает сведения об использовании.|
|**/Logger:[*uri/понятное имя*]**|Укажите средство ведения журнала результатов тестирования. Укажите параметр несколько раз, чтобы включить несколько средств ведения журнала.<br />Пример. Чтобы записать результаты в файл результатов теста Visual Studio (TRX), воспользуйтесь<br />**/Logger:trx**<br />**[;LogFileName=\<Defaults to unique file name>]**|
|**/ListTests:[*имя файла*]**|Перечисление обнаруженных тестов из указанного контейнера тестов.|
|**/ListDiscoverers**|Перечисление установленных средств обнаружения тестов.|
|**/ListExecutors**|Перечисление установленных исполнителей тестов.|
|**/ListLoggers**|Перечисление установленных средств ведения журнала тестирования.|
|**/ListSettingsProviders**|Перечисление установленных поставщиков параметров тестирования.|
|**/Blame**|Выполнение тестов в режиме обвинения. Этот параметр полезен при изоляции проблемных тестов, которые приводят к аварийному завершению хоста для тестов. При обнаружении сбоя он создает файл последовательности в `TestResults/<Guid>/<Guid>_Sequence.xml`, который фиксирует порядок тестов, выполненных до сбоя. Дополнительные сведения: [Запуск cборщика данных в режиме обвинения](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*имя файла*]**|Записывает диагностические журналы трассировки в указанный файл.|
|**/ResultsDirectory:[*path*]**|По указанному пути будет создан каталог с результатами теста, если этот путь не существует.<br />Пример: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Идентификатор родительского процесса, отвечающего за запуск текущего процесса.|
|**/Port:[*port*]**|Порт для подключения через сокет и получения сообщений о событиях.|
|**/Collect:[*dataCollector friendlyName*]**|Включает сборщик данных для тестового запуска. [Дополнительные сведения](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Регистр в параметрах и значениях не учитывается.

## <a name="examples"></a>Примеры

Синтаксис для запуска *vstest.console.exe* имеет следующий вид:

`vstest.console.exe [TestFileNames] [Options]`

Следующая команда запускает *vstest.console.exe* для библиотеки тестов *myTestProject.dll*:

```cmd
vstest.console.exe myTestProject.dll
```

Следующая команда запускает *vstest.console.exe* с множеством тестовых файлов. Для разделения имен тестовых файлов используйте пробелы.

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Следующая команда запускает *vstest.console.exe* с несколькими параметрами. Она запускает тесты в файле *myTestFile.dll* в изолированном процессе и использует параметры, заданные в файле *Local.RunSettings*. Кроме того, она запускает только тесты с меткой "Priority=1" и записывает результаты в *TRX*-файл.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Следующая команда запускает *vstest.console.exe* с параметром `/blame` для библиотеки тестов *myTestProject.dll*:

```cmd
vstest.console.exe myTestFile.dll /blame
```

В случае сбоя узла тестов создается файл *sequence.xml*. Этот файл содержит полные имена тестов в порядке их выполнения вплоть до конкретного теста, который выполнялся во время сбоя.

При отсутствии сбоя узла тестов файл *sequence.xml* не создается.

Пример созданного файла *sequence.xml*: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
