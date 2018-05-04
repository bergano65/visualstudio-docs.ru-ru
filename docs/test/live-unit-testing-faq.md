---
title: 'Функция Live Unit Testing: вопросы и ответы'
ms.date: 2017-10-03
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: c49c23bc9ca77721ba6c39fb6c94a0994a70e7d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Часто задаваемые вопросы о функции Live Unit Testing

## <a name="live-unit-testing-is-improved-and-enhanced-regularly-how-can-i-find-information-about-the-latest-new-features-and-enhancements"></a>Функция Live Unit Testing регулярно улучшается и развивается. Где найти сведения о новых возможностях и улучшениях?

**Ответ.**

Сведения о новых возможностях и улучшениях в Live Unit Testing начиная с версии 15.3 среды Visual Studio 2017 см. в статье [Новые возможности в Live Unit Testing](live-unit-testing-whats-new.md).

## <a name="what-test-frameworks-does-live-unit-testing-support-and-what-are-the-minimum-supported-versions"></a>Какие платформы тестирования поддерживает функция Live Unit Testing и каковы минимальные поддерживаемые версии?

**Ответ.**

Функция Live Unit Testing работает на трех известных платформах модульного тестирования, приведенных в таблице ниже. В этой таблице также приведены сведения о минимальной поддерживаемой версии адаптеров и платформ. Платформы модульного тестирования доступны на сайте NuGet.org.

<table>
<tr>
   <th>Тестовая платформа</th>
   <th>Минимальная версия адаптера Visual Studio</th>
   <th>Минимальная версия платформы</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio версии 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter версии 3.5.1</td>
   <td>NUnit версии 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Если у вас есть старые тестовые проекты на основе MSTest, которые ссылаются на `Microsoft.VisualStudio.QualityTools.UnitTestFramework`, и вы не хотите переходить на более новые пакеты NuGet MSTest, выполните обновление до Visual Studio 2017 версии 15.4.

В некоторых случаях, чтобы обеспечить работу Live Unit Testing, вам потребуется явным образом восстановить пакеты NuGet, на которые ссылается проект в решении. Вы можете восстановить пакеты, выполнив сборку решения явным образом (в меню верхнего уровня Visual Studio выберите **Сборка**, **Пересобрать решение**) или щелкнув решение правой кнопкой мыши и выбрав пункт **Восстановить пакеты NuGet** перед включением Living Unit Testing.

## <a name="does-live-unit-testing-work-with-net-core"></a>Совместима ли функция Live Unit Testing с проектами .NET Core?

**Ответ.**

Да. Функция Live Unit Testing совместима с .NET Core и .NET Framework. Поддержка .NET Core была недавно добавлена в Visual Studio 2017 версии 15.3. Выполните обновление до этой версии Visual Studio, если требуется поддержка Live Unit Testing для .NET Core.

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Почему функция Live Unit Testing не работает после включения?

**Ответ.**

Сведения о том, почему функция Live Unit Testing не работает, можно посмотреть в **окне вывода** (после выбора раскрывающегося меню Live Unit Testing). Эта функция может не работать по одной из следующих причин:

- Пакеты NuGet, на которые имеются ссылки в проекте, не были восстановлены. Чтобы устранить эту проблему, перед включением Live Unit Testing выполните явную сборку решения или восстановите пакеты NuGet в решении.

- При использовании в проекте тестов на основе MSTest удалите ссылку на `Microsoft.VisualStudio.QualityTools.UnitTestFramework` и добавьте ссылки на последнюю версию пакетов NuGet для MSTest, `MSTest.TestAdapter` (минимальная версия — 1.1.11) и `MSTest.TestFramework` (минимальная версия — 1.1.11). Дополнительные сведения см. в разделе "Поддерживаемые тестовые платформы" статьи [Использование Live Unit Testing в Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks).

- По крайней мере один проект в решении должен иметь ссылку на NuGet или прямую ссылку на платформу тестирования xUnit, NUnit или MSTest. Этот проект также должен иметь ссылку на соответствующий пакет NuGet для адаптера теста Visual Studio. Ссылку на адаптер теста Visual Studio можно также создать, используя файл `.runsettings`. Файл `.runsettings` должен иметь запись, аналогичную следующей:

   ```xml
    <RunSettings>
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration>
    </RunSettings>
   ```

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Почему Live Unit Testing показывает неправильный объем протестированного кода после обновления адаптера теста, на который ссылаются проекты Visual Studio, до поддерживаемой версии?

**Ответ.**

- Если несколько проектов в решении ссылаются на пакет адаптера теста NuGet, требуется обновить каждый из них до поддерживаемой версии.

- Убедитесь, что PROPS-файл MSBuild, импортированный из пакета адаптера теста, также обновлен должным образом. Проверьте версию и путь импорта для пакета NuGet, которые обычно указаны в начале файла проекта, например:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Можно ли настроить сборки Live Unit Testing?

**Ответ.**

Если для реализации инструментирования (Live Unit Testing) в решении требуется настроить дополнительные шаги, не обязательные для обычной неинструментированной сборки, вы можете добавить код в проект или целевые файлы. Этот код проверяет свойство `BuildingForLiveUnitTesting` и выполняет настраиваемые шаги перед сборкой или после нее. Вы также можете удалить определенные шаги сборки (например, публикация или создание пакетов) или добавить шаги (например, шаги для копирования) в сборку Live Unit Testing на основе этого свойства проекта. Это никак не изменит обычную сборку, а только повлияет на сборки Live Unit Testing.

Например, у вас может быть целевой объект, который создает пакеты NuGet во время обычной сборки. Вы, вероятно, не хотите, чтобы пакеты NuGet создавались после каждого внесенного изменения. Таким образом, вы можете отключить этот целевой объект в сборке Live Unit Testing, выполнив следующую команду:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Сообщения об ошибках с &lt;OutputPath&gt; или &lt;OutDir&gt;

**При попытке выполнить сборку решения с помощью Live Unit Testing отображается сообщение об ошибке, указывающее, что свойство `<OutputPath>` или `<OutDir>` задано безусловно и Live Unit Testing не будет выполнять тесты из выходной сборки. С чем это связано?**

**Ответ.**

Это может произойти, если в процессе сборки решения без проверки условий переопределяется свойство `<OutputPath>` или `<OutDir>`, после чего оно больше не является подкаталогом `<BaseOutputPath>`. В таких случаях Live Unit Testing не будет работать, так как эта функция также переопределяет эти свойства, чтобы убедиться, что артефакты сборки отправляются в папку в каталоге `<BaseOutputPath>`. Если вы должны переопределить расположение, в которое будут отправляться артефакты в обычной сборке, переопределите свойство `<OutputPath>` на основе `<BaseOutputPath>`.

Например, сборка может переопределить `<OutputPath>`, как показано ниже.

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

В этом случае ее можно заменить следующим:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```
 
Это гарантирует, что `<OutputPath>` находится в папке `<BaseOutputPath>`.

Не переопределяйте `<OutDir>` непосредственно в процессе сборки. Переопределите `<OutputPath>` вместо того, чтобы отправлять артефакты сборки в определенное расположение.
 
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Задание расположения артефактов сборки Live Unit Testing

**Я хочу, чтобы артефакты сборки Live Unit Testing отправлялись в определенное расположение, а не в расположение по умолчанию в папке `.vs`. Как это можно сделать?**

**Ответ.**

Задайте путь, где вы хотите хранить артефакты сборки Live Unit Testing, в качестве значения переменной среды уровня пользователя `LiveUnitTesting_BuildRoot`. 

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>Чем отличается выполнение тестов в окне обозревателя тестов от их выполнения с помощью функции Live Unit Testing?

**Ответ.**

Существует несколько различий:

- Во время выполнения и отладки тестов из окна обозревателя тестов используются обычные двоичные файлы, а при использовании функции Live Unit Testing — инструментированные двоичные файлы. Если вы хотите выполнить отладку инструментированных двоичных файлов, добавьте вызов метода [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) в метод теста. После этого отладчик будет запускаться во время каждого выполнения метода (в том числе когда этот метод выполняется с помощью функции Live Unit Testing), и тогда вы сможете прикрепить инструментированные двоичные файлы, а также выполнить их отладку. Тем не менее мы надеемся, что инструментирование происходит прозрачно в большинстве пользовательских сценариев, и вам не потребуется выполнять отладку инструментированных двоичных файлов.

- Функция Live Unit Testing не создает домен приложения для выполнения тестов, но при выполнении тестов в окне обозревателя тестов этот домен создается.

- Функция Live Unit Testing выполняет тесты из разных сборок последовательно, а если вы выполняете несколько тестов в окне обозревателя тестов, а затем нажимаете кнопку **Запустить тесты параллельно**, они будут выполняться параллельно.

- Для обнаружения и выполнения тестов с помощью Live Unit Testing используется `TestPlatform` версии 2, а в окне обозревателя тестов — версии 1. В большинстве случаев вы не заметите разницу. 

- Сейчас обозреватель тестов по умолчанию выполняет тесты в однопотоковом подразделении (STA), а Live Unit Testing — в многопотоковом (MTA). Чтобы выполнить тесты MSTest в однопотоковом подразделении с помощью функции Live Unit Testing, декорируйте метод теста или содержащий класс атрибутом `<STATestMethod>` или `<STATestClass>`, который находится в пакете `MSTest.STAExtensions 1.0.3-beta` NuGet. Для NUnit декорируйте метод теста атрибутом `<RequiresThread(ApartmentState.STA)>`, а для xUnit — атрибутом `<STAFact>`.

## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Как исключить из участия тесты в функции Live Unit Testing?

**Ответ.**

Пользовательские параметры см. в разделе "Добавление и исключение тестовых проектов и методов теста" статьи [Использование Live Unit Testing в Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods). Это полезно, когда необходимо выполнить конкретный набор тестов для определенного сеанса редактирования или сохранить личные настройки.
 
Для параметров, относящихся к конкретному решению, вы можете программно применить атрибут <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>, чтобы исключить методы, свойства, классы или структуры из инструментирования с помощью функции Live Unit Testing. Кроме того, чтобы исключить весь проект из инструментирования, в файле проекта для свойства `<ExcludeFromCodeCoverage>` можно задать значение `true`. Функция Live Unit Testing будет по-прежнему выполнять неинструментированные тесты, но их покрытие визуализироваться не будет.

Вы также можете проверить, отправлен ли атрибут `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` в текущий домен приложения, и на основе этого отключить тесты. Например, на тестовой платформе xUnit это можно сделать следующим образом:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Почему заголовки Win32 PE отличаются в инструментированных сборках, созданных с помощью функции Live Unit Testing?

**Ответ.**

Эта проблема исправлена и отсутствует в Visual Studio 2017 версии 15.3. Выполните обновление до этой версии Visual Studio.

Это известная ошибка прежних версий Visual Studio 2017, которая в сборках Live Unit Testing может повлиять на внедрение следующих данных заголовка Win32 PE:

- версия файла (заданная в коде параметром @System.Reflection.AssemblyFileVersionAttribute);

- значок Win32 (заданный в командной строке параметром `/win32icon:`);

- манифест Win32 (заданный в командной строке параметром `/win32manifest:`).

При выполнении тестов на основе этих значений с помощью функции Live Unit Testing может произойти сбой.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Почему функция Live Unit Testing выполняет сборку решения, даже если я не вношу никаких правок?

**Ответ.**

Это может произойти, если в процессе сборки решения создается исходный код, который является частью самого решения, а в целевых файлах сборки не указаны соответствующие входные и выходные данные. В целевых файлах необходимо определить список входных и выходных данных. За счет этого MSBuild сможет выполнять соответствующие проверки наличия обновлений и определять, требуются ли они для новой сборки.

Функция Live Unit Testing запускает сборку после обнаружения изменений в исходных файлах. Так как в процессе сборки решения создаются исходные файлы, функция Live Unit Testing переходит в бесконечный цикл сборки. Тем не менее, если проверка входных и выходных данных целевого файла выполняется, когда функция Live Unit Testing запускает вторую сборку (после обнаружения вновь созданных исходных файлов из предыдущей сборки), цикл прерывается, так как при проверке входных и выходных данных будет установлено, что обновления не требуются.  

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Как функция Live Unit Testing работает с функцией "Загрузка упрощенного решения"?

**Ответ.**

Сейчас функция Live Unit Testing не работает с функцией "Загрузка упрощенного решения". Она работает, только если загружен по меньшей мере один из тестовых проектов. До этого она не будет работать, так как функция Live Unit Testing зависит по крайней мере от одного из тестовых проектов, ссылающихся на загружаемый адаптер теста (MSTest, xUnit или NUnit).

> [!NOTE]
> В Visual Studio 2017 версии 15.5 и более поздних функция загрузки упрощенного решения недоступна. В Visual Studio 2017 версии 15.5 и выше крупные решения, содержащие управляемый код, загружаются значительно быстрее, чем раньше, даже без функции загрузки упрощенного решения.

## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Почему функция Live Unit Testing не записывает покрытие из созданного тестом процесса?

**Ответ.**

Это известная проблема, которая должна быть устранена в последующем обновлении Visual Studio 2017.

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Почему ничего не происходит после добавления или исключения тестов из набора динамического тестирования?

**Ответ.**

Эта проблема исправлена и отсутствует в Visual Studio 2017 версии 15.3. Выполните обновление до этой версии Visual Studio.

Это известная проблема для прежних версий Visual Studio 2017. Чтобы исправить эту проблему, вам нужно внести изменения в любой файл после добавления или исключения тестов. 

## <a name="live-unit-testing-and-editor-icons"></a>Значки Live Unit Testing и редактора

**Почему не отображаются какие-либо значки, даже если функция Live Unit Testing выполняет тесты (в окне вывода появляются сообщения)?**

**Ответ.**

Это происходит, если сборки, обрабатываемые функцией Live Unit Testing, по какой-либо причине не инструментированы. Например, эта функция несовместима с проектами со значением `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. В этом случае, чтобы обеспечить работоспособность функции Live Unit Testing, сборку необходимо обновить. Для этого либо удалите этот параметр, либо измените его на `true`. 

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Как собрать более подробные журналы для отчетов об ошибках файла?

**Ответ.**

Чтобы собрать более подробные журналы, выполните следующее:

- Выберите **Инструменты**, **Параметры**, **Live Unit Testing** и задайте для параметра ведения журнала значение **Подробный**. В этом случае в окне вывода будут отображаться более подробные журналы.

- В качестве значения переменной среды пользователя `LiveUnitTesting_BuildLog` задайте файл, который вы хотите использовать для сбора данных журнала MSBuild. Затем в этом файле можно просмотреть более подробные сообщения журнала MSBuild из сборок Live Unit Testing.

- Задайте для пользовательской переменной среды `LiveUnitTesting_TestPlatformLog` значение `1`, чтобы собирать журнал тестовой платформы. Теперь в файле `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` можно просмотреть подробные сообщения журнала тестовой платформы о запусках динамического модульного тестирования.

- Создайте переменную среды уровня пользователя `VS_UTE_DIAGNOSTICS` и присвойте ей значение 1 (или другое значение), а затем перезапустите Visual Studio. После этого на вкладке **Выходные данные — Тесты** в Visual Studio должно отображаться большое количество регистрируемых данных.

## <a name="see-also"></a>См. также

[Динамическое модульное тестирование](live-unit-testing.md)

