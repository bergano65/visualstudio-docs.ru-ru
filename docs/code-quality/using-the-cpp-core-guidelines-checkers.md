---
title: С помощью программы C++ основные рекомендации
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: f8b031fc1251ad06fdba154c086696337e552445
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747408"
---
# <a name="using-the-c-core-guidelines-checkers"></a>С помощью программы C++ основные рекомендации
Основные правила C++ — переносимой ряд рекомендации, правила и рекомендации о написании кода на C++, созданный специалистами C++ и конструкторы. В настоящее время Visual Studio поддерживает подмножество этих правил в рамках его средств анализа кода для C++. Средства проверки направляющих core устанавливаются по умолчанию в Visual Studio 2017 г и являются [предоставляется в виде пакета NuGet для Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Проект C++ основные рекомендации
 Создан Страуструп (Bjarne Stroustrup) и другими рекомендации основных компонентов C++ — это руководство по использованию современный язык C++ безопасно и эффективно. Рекомендации подчеркнуть статических строгая типизация и безопасность ресурсов. Они определять способы устранения или свести к минимуму наиболее ошибкам элементы языка, а также предложить как упростить код и более производительным из надежных источников. Эти правила будут обновлены на Standard C++ Foundation. Чтобы получить дополнительные сведения см. в документации [C++ основные рекомендации](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)и получить доступ к файлам проекта документации C++ основные рекомендации на [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Включить правила проверки основных C++ при анализе кода
 Можно включить анализ кода в проекте, установив **включить анализ кода в построении** флажок в **анализа кода** раздел **страницы свойств** диалоговое окно для ваш проект.

 ![Страницы свойств для настройки общих анализа кода](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 Правила проверки основных C++ представляют собой расширения наборы правил по умолчанию при включении анализа кода. Поскольку правила C++ Проверьте ядра находятся в разработке, широко применяются некоторые правила и некоторые может быть не готова для использования на весь код, но по-прежнему может быть информативной. Правила можно разделить на две группы: освобождение и экспериментальный. Можно выбрать, будет ли выполняться отмененной или экспериментальный правила в свойствах проекта.

 ![Страницы свойств для настройки расширения средств анализа кода](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Чтобы включить или отключить наборов правил проверки основных C++, откройте **страницы свойств** диалоговое окно для вашего проекта. В разделе **свойства конфигурации**, разверните **анализа кода**, **расширения**. В раскрывающемся списке элемента управления рядом с **включить C++ Core Проверьте (запущен)** или **включить C++ Core Проверьте (экспериментально)**, выберите **Да** или **нет**. Выберите **ОК** или **применить** для сохранения изменений.

## <a name="examples"></a>Примеры
 Вот некоторые из проблем, которые можно найти правила проверки основных компонентов C++:

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

 В этом примере показано несколько предупреждений, которые можно найти правила проверки основных C++:

-   C26494 — правило Type.5: всегда инициализировать объект.

-   C26485 — правило Bounds.3: нет критичной массива в указатель.

-   C26481 — правило Bounds.1: не используйте арифметических операций над указателями. Взамен рекомендуется использовать `span`.

 Если установлены и включены при компиляции кода C++ Проверьте основные наборы правил анализа кода, выводятся первые два предупреждения, но третий подавляется. Вот выходные данные сборки из примера кода:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Основные правила C++ существуют и помогает писать код лучше и безопаснее. Тем не менее если у вас есть экземпляр, где не следует применять правило или профиля, можно легко отключить его непосредственно в коде. Можно использовать `gsl::suppress` атрибут для предотвращения проверки основных C++ обнаружения и создания отчетов любое нарушение правила в следующем блоке кода. Вы можете пометить отдельные инструкции отключение определенных правил. Можно даже отключить весь профиль границы путем написания `[[gsl::suppress(bounds)]]` без включения номер конкретного правила.

## <a name="supported-rule-sets"></a>Поддерживаемые наборы правил
По мере добавления новых правил проверки основные правила C++ может увеличить количество предупреждений, созданные для существующего кода. Заранее заданные наборы правил можно использовать для фильтрации какие виды правила для включения.
Справочные разделы для большинства правил представлены в разделе [Visual Studio C++ Проверьте справочные сведения об основных](code-analysis-for-cpp-corecheck.md).

Начиная с Visual Studio 2017 г. версия 15,3 являются наборы поддерживаемых правил:
  - **Владелец указатель правила** применять [управление ресурсами проверяет, связанные с владельцем<T> от правил Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Const правила** применять [связанные const проверки от правил Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Необработанный указатель правила** применять [управление ресурсами проверяет связанные для необработанных указателей от правил Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Уникальные правила указатель** применять [управление ресурсами проверяет, относящиеся к типам с семантикой уникальный указатель от правил Core C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Ограничивает правила** применять [ограничивающий профиль основные правила C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Правила типов** применять [введите профиль основные правила C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

  **Visual Studio 2017 версии 15.5**:
  - **Класс правил** несколько правил, ориентированные на правильное использование виртуального спецификации и специальные методы. Это подмножество рекомендуется использовать для проверки [классы и иерархии классов](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
  - **Правила параллелизма** одно правило, перехватывает объекты guard объявлен неправильно. Дополнительные сведения см. в разделе [рекомендации, связанные с параллелизмом](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
  - **Правила объявления** несколько правил из [интерфейсы рекомендации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) какие сосредоточиться на том, как глобальные переменные объявляются.
  - **Функция правила** две проверки, которые помогают внедрению `noexcept` спецификатор. Это часть правила [снимите функции проектирования и реализации](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
  - **Общие правила указатель** в составе [управление ресурсами](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) применения правила, мы добавили несколько правил, определенных как общие указатели на передаваемых в функцию или использовать локально.
  - **Правил стилей** один простой, но важно check, которой эти использование [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Это первый шаг для улучшения процесса кодирования, стиль и использование выражения и операторы в C++.

  **Visual Studio 2017 версии 15.6**:
  - **Арифметических правил** правила для определения арифметические [переполнения](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [операции со знаком без](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) и [бит манипуляции](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).


 Можно ограничить предупреждения, чтобы только один или несколько групп. **Собственного минимум** и **собственного рекомендуется** правила, наборы содержат C++ Проверьте основные правила, помимо других PREfast проверок. Для просмотра доступных наборов правил, откройте диалоговое окно свойств проекта выберите **Analysis\General кода**, откройте раскрывающийся список в **наборы правил** поле со списком и подбору **выбрать несколько наборов правил** . Дополнительные сведения об использовании наборов правил в Visual Studio см. в разделе [использование наборов правил для группировки правил анализа кода](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Макросы
 Средство проверки правила C++ Core поставляется файл заголовка, который определяет макросы, которые упрощают процесс Отключение всей категории предупреждений в коде:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Эти макросы соответствуют наборов правил и развернуть в разделенный пробелами список номеров предупреждений. С помощью конструкций соответствующую директиву pragma, можно настроить эффективный набор правил, интересных для проекта или раздел кода. В следующем примере анализа кода выводит следующее предупреждение только об отсутствующих константой модификаторы.

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Атрибуты
 Компилятор Visual C++ Корпорация Майкрософт имеет ограниченную поддержку GSL отключение атрибута. Он может использоваться для подавления предупреждений для выражения и блок инструкций внутри функции.

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
 Вместо #pragmas можно использовать параметры командной строки на странице свойств файла для подавления предупреждений для проекта или отдельного файла. Например, чтобы отключить предупреждение 26400 для файла:

 1) Щелкните правой кнопкой мыши файл в **обозревателе решений**

 2) Выберите **свойства | C / C++ | Командная строка**

 3) В **Дополнительные параметры** окна, добавление `/wd26400`.

 Параметр командной строки можно использовать для временного отключения всех анализа кода для файла, указав `/analyze-`. При этом создается предупреждение *D9025 переопределение «/ analyze» с "/ analyze-"*, который напоминает о необходимости повторно включить анализ кода в более поздней версии.

 ## <a name="corecheck_per_file"></a> Включение проверки правила Core C++ для конкретного проекта файлов
Иногда может быть полезным с фокусом ввода выполните анализ кода и по-прежнему использовать интегрированную среду разработки Visual Studio. Следующий пример можно использовать для крупных проектов сэкономить время построения и упростить результаты фильтрации:

1.  В командной оболочке задать `esp.extension` и `esp.annotationbuildlevel` переменные среды.
2.  Чтобы унаследовать эти переменные, запустите Visual Studio из командной оболочки.
3.  Загрузить проект и откройте его свойства.
4.  Включить анализ кода, выберите соответствующее правило наборов, но не включайте расширения средств анализа кода.
5.  Перейдите к файлу, который нужно анализировать с помощью проверки C++ основные рекомендации и откройте его свойства.
6.  Выберите **C / C++ \Command параметры строки** и добавьте `/analyze:plugin EspXEngine.dll`
7.  Отключение использования предкомпилированного заголовка (**C / C++ \Precompiled заголовки**). Это необходимо, поскольку подсистема расширения может пытаться выполнить операцию чтения внутренние сведения из предкомпилированного заголовка (PCH); Если предкомпилированный заголовок скомпилирован с параметрами по умолчанию проекта, он будет несовместим.
8.  Перестройте проект. Общие PREFast проверки следует выполнить на всех файлов. Так как средство проверки готовности C++ основные рекомендации по умолчанию не включена, ее следует запускать только файла, которая настроена на его использование.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Как использовать средство проверки правила C++ Core вне Visual Studio
Основные правила C++ проверки можно использовать в автоматических построениях.

### <a name="msbuild"></a>MSBuild
 Анализ машинного кода проверки (PREfast) интегрирована в среде MSBuild с пользовательской целевых файлов. Можно использовать свойства проекта, чтобы включить его и добавить средство проверки правила основных компонентов C++ (на котором основан PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Убедитесь в том, что вы добавляете эти свойства перед импортом файла Microsoft.Cpp.targets. Выбор наборов правил конкретных или создать настраиваемый набор правил можно использовать набор правил по умолчанию, который включает другие PREfast проверки.

Можно выполнить проверки основных C++ только на указанных файлов с таким же образом, как [описанных ранее](#corecheck_per_file), но с помощью MSBuild файлов. Переменные среды можно задать с помощью `BuildMacro` элемента:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Если не нужно изменять файл проекта можно передавать свойства в командной строке:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Проекты не MSBuild
Если используется система сборки, которая не зависит от MSBuild можно запустить средство проверки готовности, но необходимо ознакомиться с некоторые возможности конфигурация ядра анализа кода. Эти возможности не обязательно будет поддерживаться в будущем.

Необходимо задать несколько переменных среды и используйте соответствующие параметры командной строки для компилятора. Лучше работать в среде «собственного средства командной строки», чтобы не нужно искать определенные пути для компилятора, включаемых каталогов и т. д.

1.  **Переменные среды**
  - `set esp.extensions=cppcorecheck.dll` Подсистема для загрузки модуля C++ основные рекомендации.
  - `set esp.annotationbuildlevel=ignore` Это приведет к отключению логику, которая обрабатывает заметки SAL. Заметки не влияют на анализ кода программы C++ основные правила проверки, но их обработки времени (иногда длительное время). Этот параметр является обязательным, но настоятельно рекомендуется.
  - `set caexcludepath=%include%` Корпорация Майкрософт рекомендует отключить предупреждения, которые срабатывают в стандартные заголовки. Можно добавить другие пути, например путь к общих заголовков в проекте.
2.  **Параметры командной строки**
  - `/analyze`  Включает анализ кода (рекомендуется также использовать / analyze: только и / analyze: quiet).
  - `/analyze:plugin EspXEngine.dll` Этот параметр загружает подсистему расширения средств анализа кода в PREfast. Этот модуль, в свою очередь, загружает средство проверки готовности C++ основные рекомендации.



## <a name="use-the-guideline-support-library"></a>Использование библиотеки поддержки направляющих
 Библиотека поддержки направляющих поможет придерживаться следующих основных правил. GSL содержит определения, которые позволяют замените ошибок конструкции более безопасные альтернативы. Например, можно заменить `T*, length` пару параметров с `span<T>` типа. Найти по адресу GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Библиотека является открытым исходным кодом, для просмотра источников, добавление комментариев или участие. Проект можно найти в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Следуйте рекомендациям проверьте Core C++ в проектах Visual Studio 2015
  Если вы используете Visual Studio 2015, проверьте C++ основных наборов правил анализа кода не устанавливаются по умолчанию. Необходимо выполнить некоторые дополнительные действия, чтобы можно было включить C++ Проверьте основных средств анализа кода в Visual Studio 2015. Корпорация Майкрософт обеспечивает поддержку для проектов Visual Studio 2015 с помощью пакета Nuget. Пакет называется Microsoft.CppCoreCheck, и он доступен по [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Для этого пакета необходимо иметь по крайней мере установленной среды Visual Studio 2015 с обновлением 1.

 Пакет также устанавливает другой пакет как зависимость только заголовков направляющих поддержки библиотеки (GSL). GSL доступна также на github на сайте [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Из-за того, в который загружаются правил анализа кода необходимо установить пакет Microsoft.CppCoreCheck NuGet в каждый проект C++, который требуется проверить в Visual Studio 2015.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Чтобы добавить пакет Microsoft.CppCoreCheck свой проект в Visual Studio 2015

1.  В **обозревателе решений**, щелкните правой кнопкой мыши, чтобы открыть контекстное меню проекта в решение, которое вы хотите добавить пакет. Выберите **управление пакетами NuGet** Открытие **диспетчера пакетов NuGet**.

2.  В **диспетчера пакетов NuGet** найдите Microsoft.CppCoreCheck.

     ![В окне диспетчера пакетов NuGet отображаются CppCoreCheck пакета](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Выберите пакет Microsoft.CppCoreCheck, а затем выберите **установить** кнопку, чтобы добавить правила в проект.

 Пакет NuGet добавляет дополнительные MSBuild *.targets* файл в проект, который вызывается при включении анализа кода в проекте. Это *.targets* файла добавляет правила проверки основных компонентов C++ как расширение дополнительные средства анализа кода Visual Studio. При установке пакета можно использовать для включения или отключения правила освобождение и экспериментальный диалоговое окно страниц свойств.

## <a name="see-also"></a>См. также
[Visual Studio справочные сведения об основных C++ проверки](code-analysis-for-cpp-corecheck.md).

