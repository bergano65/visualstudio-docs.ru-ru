---
title: "Часто задаваемые вопросы о функции Live Unit Testing | Документация Майкрософт"
ms.date: 2017-03-13
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 2a58b84403189d824494af85bc732a1b8cf3d0b6
ms.contentlocale: ru-ru
ms.lasthandoff: 07/11/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Часто задаваемые вопросы о функции Live Unit Testing

## <a name="does-live-unit-testing-work-with-net-core"></a>Совместима ли функция Live Unit Testing с проектами .NET Core?  

**Ответ.**

Да. Функция Live Unit Testing совместима с .NET Core и .NET Frameworks. Поддержка .NET Core была недавно добавлена в предварительную версию 15.3 Visual Studio 2017. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Почему функция Live Unit Testing не работает после включения? 

**Ответ.** 

Сведения о том, почему функция Live Unit Testing не работает, можно посмотреть в **окне вывода** (после выбора раскрывающегося меню Live Unit Testing). Эта функция может не работать по одной из следующих причин: 

- Пакеты NuGet, на которые имеются ссылки в проекте, не были восстановлены. Чтобы устранить эту проблему, перед включением Live Unit Testing выполните явную сборку решения или восстановите пакеты NuGet в решении. 

- При использовании в проекте тестов на основе MSTest удалите ссылку на `Microsoft.VisualStudio.QualityTools.UnitTestFramework` и добавьте ссылки на последнюю версию пакетов NuGet для MSTest, `MSTest.TestAdapter` (минимальная версия — 1.1.11) и `MSTest.TestFramework` (минимальная версия — 1.1.11). Дополнительные сведения см. в разделе "Поддерживаемые тестовые платформы" статьи [Функция Live Unit Testing в Visual Studio 2017](live-unit-testing.md#supported-test-frameworks).
 
- По крайней мере один проект в решении должен иметь ссылку на NuGet или прямую ссылку на тестовую платформу xUnit, NUnit или MSTest. Этот проект также должен иметь ссылку на соответствующий пакет NuGet для адаптера теста Visual Studio. Ссылку на адаптер теста Visual Studio можно также создать, используя файл `.runsettings`. Файл `.runsettings` должен иметь запись, аналогичную следующей: 

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

Пользовательские параметры см. в разделе "Добавление и исключение тестовых проектов и методов теста" статьи [Функция Live Unit Testing в Visual Studio 2017](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods). Это очень полезно, когда необходимо выполнить конкретный набор тестов для определенного сеанса редактирования или сохранить личные настройки.
  
Для параметров, относящихся к конкретному решению, вы можете программно применить атрибут <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>, чтобы исключить методы, свойства, классы или структуры из инструментирования с помощью функции Live Unit Testing. Кроме того, чтобы исключить весь проект из инструментирования, в файле проекта для свойства `<ExcludeFromCodeCoverage>` можно задать значение `true`. Функция Live Unit Testing будет по-прежнему выполнять неинструментированные тесты, но их покрытие визуализироваться не будет.

Вы также можете проверить, отправлен ли атрибут `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` в текущий домен приложения, и на основе этого отключить тесты. Например, на тестовой платформе xUnit это можно сделать следующим образом:

```cs
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

Это известная ошибка, которая в сборках Live Unit Testing может повлиять на внедрение следующих данных заголовка Win32 PE: 

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

Сейчас Live Unit Testing не работает должным образом с функцией "Загрузка упрощенного решения", если все проекты в решении еще не загружены. В таких случаях вы можете получить неверные данные о покрытии.
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Почему функция Live Unit Testing не записывает покрытие из созданного тестом процесса?
 
**Ответ.**

Это известная проблема, которую не удалось исправить в выпуске Visual Studio 2017. Мы планируем исправить ее в последующем обновлении Visual Studio 2017. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Почему ничего не происходит после добавления или исключения тестов из набора динамического тестирования? 

**Ответ.**

Это известная проблема. Чтобы исправить ее, вам потребуется внести изменения в любой файл после добавления или исключения тестов.  

## <a name="live-unit-testing-and-editor-icons"></a>Значки Live Unit Testing и редактора 

**Почему не отображаются какие-либо значки, даже если функция Live Unit Testing выполняет тесты (в окне вывода появляются сообщения)?** 

**Ответ.**

Это происходит, если сборки, обрабатываемые функцией Live Unit Testing, по какой-либо причине не инструментированы. Например, эта функция несовместима с проектами со значением `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. В этом случае, чтобы обеспечить работоспособность функции Live Unit Testing, процесс сборки необходимо обновить, либо удалив этот параметр, либо изменив его на `true`.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Как собрать более подробные журналы для отчетов об ошибках файла? 

**Ответ.**

Чтобы собрать более подробные журналы, выполните следующее: 

- Выберите **Инструменты**, **Параметры**, **Live Unit Testing** и задайте для параметра ведения журнала значение **Подробный**. В этом случае в окне вывода будут отображаться более подробные журналы. 

- В качестве значения переменной среды пользователя `LiveUnitTesting_BuildLog` задайте файл, который вы хотите использовать для сбора данных журнала MSBuild. Затем в этом файле можно просмотреть более подробные сообщения журнала MSBuild из сборок Live Unit Testing.

- Задайте для пользовательской переменной среды `LiveUnitTesting_TestPlatformLog` значение `1`, чтобы собирать журнал тестовой платформы. Теперь в файле `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` можно просмотреть подробные сообщения журнала тестовой платформы о запусках динамического модульного тестирования.

- Создайте переменную среды уровня пользователя `VS_UTE_DIAGNOSTICS` и присвойте ей значение 1 (или другое значение), а затем перезапустите Visual Studio. После этого на вкладке **Выходные данные — Тесты** в Visual Studio должно отображаться большое количество регистрируемых данных. 
 
## <a name="see-also"></a>См. также

[Динамическое модульное тестирование](live-unit-testing.md)
 

