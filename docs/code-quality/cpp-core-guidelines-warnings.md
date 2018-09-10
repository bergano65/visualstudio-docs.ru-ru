---
title: Предупреждения C++ Core Guidelines
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- cplusplus
ms.openlocfilehash: 035f1fe305576eb7f5bf05fb6cc5f6343e256dca
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279754"
---
# <a name="using-the-c-core-guidelines-checkers"></a>С помощью средства проверки C++ Core Guidelines
C++ Core Guidelines представляют собой переносимый набор рекомендации, правила и рекомендации о написании кода на C++, созданные экспертами C++ и конструкторы. В настоящее время Visual Studio поддерживает подмножество этих правил как часть его средств анализа кода для C++. Средства проверки рекомендация core устанавливаются по умолчанию в Visual Studio 2017 и являются [предоставляется в виде пакета NuGet для Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Проект C++ Core Guidelines
 Создан (Bjarne Stroustrup) и другими C++ Core Guidelines — это руководство по использованию современный C++, безопасно и эффективно. Рекомендации подчеркнуть статический строгая типизация и безопасность ресурсов. Они определять способы устранить или свести к минимуму наиболее подверженных ошибкам части языка и предлагают способы сделать код более простой и более высокую производительность надежным способом. Эти рекомендации обслуживаются Standard C++ Foundation. Дополнительные сведения см. в документации [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)и получить доступ к документации файлов проекта C++ Core Guidelines на [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Включить правила C++ Core Check в анализе кода
 Вы можете включить анализ кода в проекте, выбрав **включить анализ кода в построении** флажок в **анализа кода** раздел **страницы свойств** диалоговое окно для ваш проект.

 ![Страница свойств для параметров общие анализа кода](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 Правила C++ Core Check представляют собой расширения наборы правил по умолчанию при включении анализа кода. Поскольку эти правила C++ Core Check в стадии разработки, широко применяются некоторые правила, а некоторые могут быть не готовы для использования на весь код, но по-прежнему может быть информативной. Правила можно разделить на две группы: выпущено и экспериментальных. Можно выбрать, следует ли выполнять правила отмененной или экспериментальный в свойствах проекта.

 ![Страница свойств для параметров расширения анализа кода](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Чтобы включить или отключить наборов правил C++ Core Check, откройте **страницы свойств** диалоговое окно для вашего проекта. В разделе **свойства конфигурации**, разверните **анализа кода**, **расширения**. В раскрывающемся списке элемента управления рядом с полем **включить C++ Core Check (запущен)** или **включить C++ Core Check (экспериментальная функция)**, выберите **Да** или **нет**. Выберите **ОК** или **применить** для сохранения изменений.

## <a name="examples"></a>Примеры
 Вот некоторые из проблем, которые можно найти правила C++ Core Check примером:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

 В этом примере показаны некоторые из предупреждений, которые можно найти правила C++ Core Check:

-   C26494 — правило Type.5: всегда Инициализируйте объект.

-   C26485 — правило Bounds.3: нет decay массива в указатель.

-   C26481 — правило Bounds.1: не используйте арифметику указателей. Взамен рекомендуется использовать `span`.

 Если установлены и включены при компиляции кода C++ Core Check наборы правил анализа кода, первые два предупреждения выводятся, но третий подавляется. Ниже приведен результат сборки из образца кода.

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Core Guidelines должны помогать вам в написании кода лучше и безопаснее. Тем не менее если у вас есть экземпляр, где не должно применяться правило или профиля, можно легко отключить его непосредственно в коде. Можно использовать `gsl::suppress` атрибут для предотвращения C++ Core Check обнаружения и создания отчетов любое нарушение правила в нем следующий блок кода. Можно пометить отдельные инструкции, чтобы отключить определенные правила. Можно даже отключить весь профиль границы, написав `[[gsl::suppress(bounds)]]` без включения номер конкретного правила.

## <a name="supported-rule-sets"></a>Поддерживаемые наборы правил
Правила проверки C++ Core добавляются новые правила, может увеличить число предупреждений, которые создаются для существующего кода. Заранее заданные наборы правил можно использовать для фильтрации какие типы правил для поддержки. Начиная с Visual Studio 2017 версии 15.3 являются наборы поддерживаемых правил:
  - **Правила для указателей владельцев** применять [управления ресурсами проверяет, связанные с owner<T> из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Правила для констант** применять [проверки, связанные с const, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Правила для необработанных указателей** применять [управления ресурсами проверяет связанные с необработанных указателей, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Правила для уникальных указателей** применять [управления ресурсами проверяет, связанные с типами с семантикой уникальных указателей, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Правила проверки границ** применять [ограничивающий профиль из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Правила типов** применять [введите профиля, из C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).


 Вы можете ограничить предупреждения, чтобы только один или несколько групп. **Собственного минимум** и **собственного рекомендуется** правило, включают правила C++ Core Check в дополнение к другим PREfast проверок. Для просмотра доступных наборов правил, откройте диалоговое окно свойств проекта выберите **Analysis\General кода**, откройте раскрывающийся список в **наборы правил** поле со списком и выбора **выбрать несколько наборов правил** . Дополнительные сведения об использовании наборов правил в Visual Studio, см. в разделе [использование наборов правил для группировки правил анализа кода](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Макросы
 Проверка правила C++ Core поставляется с файлом заголовка, который определяет макросы, которые упрощают процесс для подавления всей категории предупреждений в коде:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Эти макросы соответствуют наборов правил и разверните в разделенный пробелами список номеров предупреждений. С помощью конструкций соответствующие директивы pragma можно настроить эффективный набор правил интересные для проекта или кода. В следующем примере анализ кода только предупреждает об отсутствует постоянное модификаторы:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Атрибуты
 Компилятор Microsoft Visual C++ имеет ограниченную поддержку для GSL подавлять атрибута.
Его можно использовать для подавления предупреждений для выражений и инструкций блока внутри функции.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Подавление анализа с помощью параметров командной строки
 Вместо #pragmas Чтобы отключить предупреждения для проекта или отдельного файла можно использовать параметры командной строки на странице свойств файла. Например, чтобы отключить предупреждения 26400 для файла:

 1) Щелкните правой кнопкой мыши файл в **обозревателе решений**

 2) Выберите **свойства | C / C++ | Командная строка**

 3) В **Дополнительные параметры** окна, добавление `/wd26400`.

 Можно использовать параметр командной строки будет временно отключить анализатора кода для файла путем указания `/analyze-`. Это выдает предупреждение *D9025 переопределение «/ analyze» с "/ analyze-"*, который будет напоминать о необходимости снова включить анализ кода в более поздней версии.

 ## <a name="corecheck_per_file"></a> Включение правила C++ Core Checker для конкретного проекта файлов
Иногда может быть полезно для анализа кода с фокусом ввода и по-прежнему использовать Visual Studio IDE. Ниже приведен пример сценария, который может использоваться для крупных проектов для экономии времени сборки и облегчают фильтра результатов.
1.  В командной строке задайте `esp.extension` и `esp.annotationbuildlevel` переменные среды.
2.  Запустите Visual Studio из командной оболочки для наследования эти переменные.
3.  Загрузить проект и откройте ее свойства.
4.  Включить анализ кода, выбрать наборы соответствующее правило, но не включайте расширения анализа кода.
5.  Перейдите к файлу, который вы хотите проанализировать с помощью правила C++ Core Checker и откройте ее свойства.
6.  Выберите **C / C++ \Command параметры строки** и добавьте `/analyze:plugin EspXEngine.dll`
7.  Отключить использование файла предкомпилированного заголовка (**C / C++ \Precompiled заголовки**). Это необходимо, так как подсистема расширений может попытаться прочитать внутренние сведения из файла предкомпилированного заголовка и если последний был скомпилирован с параметрами по умолчанию проекта, он не будут совместимы.
8.  Перестройте проект. Распространенные PREFast проверки должны работать на всех файлов. Так как правила C++ Core Checker не включена по умолчанию, он должен выполняться только на файл, который настроен для использования его.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Как использовать правила C++ Core Checker вне Visual Studio
Можно использовать проверки C++ Core Guidelines в автоматических построениях.

### <a name="msbuild"></a>MSBuild
 Средство проверки анализ машинного кода (PREfast) интегрируется в среду MSBuild файлами пользовательских целевых объектов. Можно использовать свойства проекта, чтобы включить его и добавить C++ Core Checker рекомендации (который основан на PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Убедитесь, что можно добавить эти свойства перед импортом файла Microsoft.Cpp.targets. Можно выбрать наборы конкретное правило или создать настраиваемый набор правил или использовать набор правил по умолчанию, который включает в себя другие PREfast проверки.

C++ Core Checker можно запустить только на указанные файлы, используя тот же подход, как [описанные ранее](#coreckeck_per_file), но с помощью файлов MSBuild. Переменные среды можно задать с помощью `BuildMacro` элемента:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Если вы не хотите изменять файл проекта, свойства можно передать в командной строке:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Проекты, отличных от MSBuild
Если вы используете систему сборки, не зависящая от MSBuild можно запустить средство проверки, но вам потребуется ознакомиться с некоторые внутренние компоненты, анализ кода конфигурации ядра (которое не обязательно будет поддерживаться в будущем).

Необходимо будет установить несколько переменных среды и использовать параметрах командной строки для компилятора. Лучше работать в среде «Командная строка Native Tools», чтобы у вас нет для поиска для конкретных путей для компилятора, включают каталоги и т. д.

1.  **Переменные среды**
  - `set esp.extensions=cppcorecheck.dll` Подсистема для загрузки модуля C++ Core Guidelines.
  - `set esp.annotationbuildlevel=ignore` Это отключает логику, которая обрабатывает заметки SAL. Заметки не влияют на анализ кода в правила C++ Core Checker, но их обработка занимает время (иногда много времени). Этот параметр является необязательным, но настоятельно рекомендуется.
  - `set caexcludepath=%include%` Мы настоятельно рекомендуем отключить предупреждения, которые срабатывают на стандартные заголовки. Можно добавить дополнительные пути, например путь к общие заголовки в проекте.
2.  **Параметры командной строки**
  - `/analyze`  Включает анализ кода (включая / analyze: только и / analyze: quiet).
  - `/analyze:plugin EspXEngine.dll` Этот параметр, загружает модуль расширения анализа кода в PREfast. Этот модуль, в свою очередь, загружает правила C++ Core Checker.



## <a name="use-the-guideline-support-library"></a>Использование библиотеки поддержки рекомендации
 Библиотека поддержки рекомендация призвана обеспечить следование основных рекомендаций. GSL содержит определения, которые позволяют заменять ошибкам конструкции с более безопасные альтернативы. Например, можно заменить `T*, length` пары параметров с `span<T>` типа. Найти по адресу GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Библиотека является открытым исходным кодом, чтобы просмотреть источники, добавлять комментарии или участие. Проект можно найти в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Использовать правила C++ Core Check в проектах Visual Studio 2015
  Если вы используете Visual Studio 2015, C++ Core Check наборов правил анализа кода не устанавливаются по умолчанию. Необходимо выполнить некоторые дополнительные действия, чтобы можно было включить средства анализа кода C++ Core Check, в Visual Studio 2015. Корпорация Майкрософт предоставляет поддержку для проектов Visual Studio 2015 с помощью пакета Nuget. Пакет называется Microsoft.CppCoreCheck, и оно доступно в [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Этот пакет требует, что у вас есть по крайней мере установлена среда Visual Studio 2015 с обновлением 1.

 Пакет также устанавливает другой пакет как зависимость только заголовки рекомендация поддержки библиотеки (GSL). GSL также доступна на сайте GitHub в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Из-за того, в который загружаются правил анализа кода необходимо установить пакет Microsoft.CppCoreCheck NuGet в каждый проект C++, который вы хотите проверить в Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Добавление пакета Microsoft.CppCoreCheck в проект в Visual Studio 2015

1.  В **обозревателе решений**, щелкните правой кнопкой мыши, чтобы открыть контекстное меню проекта в решении, которое вы хотите добавить пакет. Выберите **управление пакетами NuGet** открыть **диспетчер пакетов NuGet**.

2.  В **диспетчер пакетов NuGet** окно, и выполните поиск Microsoft.CppCoreCheck.

     ![Окно диспетчера пакетов NuGet показан пакет CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Выберите пакет Microsoft.CppCoreCheck, а затем выберите **установить** кнопку, чтобы добавить правила в проект.

 Пакет NuGet добавляет дополнительный файл целевых объектов MSBuild в проект, который вызывается при включении анализа кода в проекте. Этот файл .targets добавляет правила C++ Core Check как расширение дополнительные средства анализа кода в Visual Studio. При установке пакета, можно использовать диалоговое окно страниц свойств для включения или отключения правила выпущенных и экспериментальных.

