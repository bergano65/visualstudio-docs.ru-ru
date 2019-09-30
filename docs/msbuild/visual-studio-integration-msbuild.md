---
title: Интеграция Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00d64b060b340302107ddffaf1d69cad802a283b
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913276"
---
# <a name="visual-studio-integration-msbuild"></a>Интеграция Visual Studio (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] размещается в Visual Studio для загрузки и сборки управляемых проектов. Поскольку [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] отвечает за проект, в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] можно успешно использовать практически любой проект в формате [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], даже если проект был создан с помощью другого инструмента и участвует в процессе пользовательского построения.

 В данной статье рассматриваются конкретные аспекты размещения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] продуктом [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], которые необходимо учитывать при настройке проектов и файлов в формате *.targets*, которые требуется загрузить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с последующей сборкой. Это поможет вам обеспечить наличие в настраиваемом проекте таких функций [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , как IntelliSense и отладка.

 Дополнительные сведения о проектах C++ см. в статье [Файлы проекта](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Расширения имени файла проекта
 Файл *MSBuild.exe* распознает любое расширение имени файла проекта, если оно соответствует шаблону *.\*proj*. Однако [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] распознает только подмножество расширений этих имен файлов проекта, определяющее языковую систему проекта, которая будет загружать проект. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не имеет не зависящей от языка системы проекта, основанной на использовании [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .

 Например, система проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] загружает файлы формата *.csproj*, но [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не может загружать файлы формата *.xxproj*. Файл проекта для исходных файлов на любом языке должен использовать то же самое расширение, что и файлы проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , чтобы их можно было загрузить в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="well-known-target-names"></a>Известные имена целевых файлов
 При выборе команды **Build** в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] происходит выполнение целевого файла, который используется в проекте по умолчанию. Этот целевой объект часто называется также `Build`. При выборе команды **Перестроить** или **Очистить** делается попытка выполнить целевой файл с тем же именем в проекте. При выборе команды **Опубликовать** происходит выполнение целевого файла с именем `PublishOnly` в проекте.

## <a name="configurations-and-platforms"></a>Конфигурации и платформы
 Конфигурации представлены в проектах [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] свойствами, сгруппированными в элемент `PropertyGroup` , который имеет атрибут `Condition` . [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] анализирует эти условия, чтобы создать отображаемый список конфигураций и платформ проекта. Чтобы можно было успешно получить этот список, соответствующие условия должны иметь формат, аналогичный следующему:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 С этой целью[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проверяет условия в `PropertyGroup`, `ItemGroup`, `Import`, свойствах и элементах объекта.

## <a name="additional-build-actions"></a>Дополнительные действия при сборке
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] дает возможность изменить имя типа элемента файла в проекте с помощью свойства **Действие при сборке** в окне **Свойства файла**. В этом меню имена типов элементов **Compile**, **EmbeddedResource**, **Content** и **None** всегда приводятся наряду со всеми другими именами типов элементов, которые уже используются в проекте. Чтобы быть уверенным в том, что в этом меню всегда будут доступны все пользовательские имена типов элементов, эти имена можно добавлять к типу элемента под названием `AvailableItemName`. Например, при добавлении следующих имен к файлу проекта одновременно будет добавлен пользовательский тип **JScript** к этому меню для всех проектов, которые его импортируют:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Некоторые имена типов элементов являются особыми для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , но они не приводятся в раскрывающемся меню.

## <a name="in-process-compilers"></a>Внутрипроцессные компиляторы
 Если возможно, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет пытаться использовать внутрипроцессную версию компилятора [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] для повышения производительности. (Неприменимо к [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) Чтобы при этом была обеспечена правильная работа, должны быть выполнены следующие условия:

- Среди целевых объектов проекта должна быть задача под названием `Vbc` для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

- Для параметра `UseHostCompilerIfAvailable` этой задачи должно быть установлено значение "true".

## <a name="design-time-intellisense"></a>Функция IntelliSense в режиме разработки
 Чтобы получить поддержку IntelliSense в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] до того, как будет создана конечная сборка, должны выполняться следующие условия:

- Должен существовать целевой объект с именем `Compile`.

- Либо целевой объект `Compile` , либо одна из его зависимостей должны вызывать задачу компилятора для проекта, например `Csc` или `Vbc`.

- Либо целевой объект `Compile` , либо одна из его зависимостей должны инициировать получение компилятором всех необходимых параметров для IntelliSense, особенно всех ссылок.

- Должны выполняться условия, указанные в разделе [Внутрипроцессные компиляторы](#in-process-compilers).

## <a name="build-solutions"></a>Создание решений
 В пределах [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]управление файлом решения и заказом на построение проекта осуществляется самим продуктом [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Если построение решения осуществляется с помощью *msbuild.exe* в командной строке, то [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполняет синтаксический разбор файла решения и дает указание на выполнение построения проекта. В обоих случаях проекты строятся по отдельности в порядке зависимости, и взаимные ссылки между проектами не отслеживаются. В противоположность этому, при построении отдельных проектов с помощью *msbuild.exe* взаимные ссылки между проектами отслеживаются.

 Если построение осуществляется внутри [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], свойству `$(BuildingInsideVisualStudio)` назначается значение `true`. Это можно использовать при работе с файлами проекта или с файлами в формате *.targets*, если нужно, чтобы построения вели себя по-разному.

## <a name="display-properties-and-items"></a>Отображение свойств и элементов
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] распознает имена и значения некоторых свойств. Например, следующее свойство проекта вызывает появление названия **приложения Windows** в поле **Тип приложения** в **конструкторе проектов**.

```xml
<OutputType>WinExe</OutputType>
```

 Значение этого свойства можно изменить в **конструкторе проектов** и сохранить в файле проекта. Если такому свойству присвоено недопустимое значение при вводе вручную, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] выведет предупреждение при загрузке проекта и заменит недопустимое значение на значение по умолчанию.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] распознает значения по умолчанию для некоторых свойств. Значения этих свойств будут вставляться в файл проекта только в том случае, если они отличаются от значений по умолчанию.

 Свойства, имеющие произвольные имена, не отображаются в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Чтобы изменить произвольно заданное имя в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], нужно открыть файл проекта в XML-редакторе и вручную изменить его. Дополнительные сведения см. в разделе [Editing Project Files in Visual Studio](#edit-project-files-in-visual-studio) (Изменение файлов проектов в Visual Studio) ниже.

 Элементы, определенные в проекте с произвольными именами типов элементов, по умолчанию отображаются в **обозревателе решений** в соответствующем узле проекта. Чтобы скрыть элемент, установите значение `Visible` метаданных `false`. Например, указанный ниже элемент будет участвовать в процессе построения, но не будет отображаться в **обозревателе решений**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

 По умолчанию не отображаются элементы, которые объявлены в файлах, импортированных в проект. В **обозревателе решений** никогда не отображаются элементы, созданные в процессе построения.

## <a name="conditions-on-items-and-properties"></a>Условия, накладываемые на элементы и свойства
 В процессе построения полностью учитываются все условия.

 При определении отображаемого значения свойства те свойства, которые продуктом [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] рассматриваются как зависящие от конфигурации, оцениваются не так, как свойства, которые считаются не зависящими от конфигурации. Для свойств, которые считаются зависящими от конфигурации, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливает соответствующие свойства `Configuration` и `Platform` и дает указание [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] еще раз оценить проект. Для свойств, которые считаются не зависящими от конфигурации, определенного способа оценки условий не предусмотрено.

 При решении, следует ли отображать данный элемент в **обозревателе решений**, условные выражения с участием элементов всегда игнорируются.

## <a name="debugging"></a>Отладка
 Чтобы найти и запустить выходную сборку с присоединением отладчика, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] требуется, чтобы были правильно заданы свойства `OutputPath`, `AssemblyName`и `OutputType` . Присоединение отладчика невозможно, если в процессе сборки компилятор не создал файл *.pdb*.

## <a name="design-time-target-execution"></a>Выполнение целевых объектов в режиме разработки
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пытается запустить выполнение целевых объектов с определенными именами при загрузке проекта. Эти целевые объекты включают в себя `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` и `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] запускает эти целевые объекты, что позволяет инициализировать компилятор, который обеспечивает функционирование IntelliSense. Возможна также инициализация отладчика и разрешение ссылок, отображаемых в обозревателе решений. Если эти целевые объекты отсутствуют, то загрузка и построение проекта будут выполняться правильно, но работа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в режиме разработки будет иметь функциональные ограничения.

## <a name="edit-project-files-in-visual-studio"></a>Изменение файлов проектов в Visual Studio
 Чтобы изменить непосредственно проект [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , можно открыть файл проекта в XML-редакторе Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Выгрузка и изменение файла проекта в Visual Studio

1. В **обозревателе решений**откройте контекстное меню для своего проекта и выберите **Выгрузить проект**.

     К проекту добавляется пометка **(недоступный)** .

2. В **обозревателе решений** откройте контекстное меню для недоступного проекта и выберите **Изменить \<файл проекта>** .

     В XML-редакторе Visual Studio открывается файл проекта.

3. Измените, сохраните и закройте файл проекта.

4. В **обозревателе решений**откройте контекстное меню для недоступного проекта и выберите **Перезагрузить проект**.

## <a name="intellisense-and-validation"></a>IntelliSense и проверка
 При использовании XML-редактора для изменения файлов проекта работой IntelliSense и функции проверки управляют файлы схемы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . Они устанавливаются в кэш схемы, который можно найти по следующему пути *\<каталог установки Visual Studio>\Xml\Schemas\1033\MSBuild*.

 Типы ядра [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] определяются в *Microsoft.Build.Core.xsd*, а стандартные типы, используемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], определяются в *Microsoft.Build.CommonTypes.xsd*. Чтобы настроить схемы таким образом, чтобы выполнялась функция IntelliSense и проверка пользовательских имен типов элементов, а также свойств и задач, можно либо изменить *Microsoft.Build.xsd*, либо создать собственную схему, включающую схемы CommonTypes или Core. Если создается собственная схема, необходимо с помощью XML-редактора найти ее, используя окно **Свойства** .

## <a name="edit-loaded-project-files"></a>Правка загруженных файлов проектов
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отправляет в кэш содержимое файлов проектов и файлов, импортированных файлами проекта. Если вы изменяете загруженный файл проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически напомнит еще раз загрузить проект, чтобы изменения вступили в силу. Однако, если вы изменяете файл, импортированный загруженным проектом, напоминание о перезагрузке не появится, и необходимо будет вручную выгрузить и еще раз загрузить проект, чтобы изменения вступили в силу.

## <a name="output-groups"></a>Выходные группы
 Имена некоторых целевых объектов, определенных в *Microsoft.Common.targets*, оканчиваются на `OutputGroups` или `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вызывает эти целевые объекты, чтобы они получили особые списки выходных данных проекта. Например, целевой объект `SatelliteDllsProjectOutputGroup` создает список всех сопутствующих сборок, которые будут созданы в процессе построения. Эти выходные группы используются, например, такими функциями, как опубликование, развертывание и взаимные ссылки между проектами. Проекты, в которых они не определены, будут загружать и строить их в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], но при этом отдельные функции могут работать неправильно.

## <a name="reference-resolution"></a>Разрешение ссылок
 Разрешение ссылок — это процесс использования элементов ссылки, которые хранятся в файле проекта, для определения местоположения реальных сборок. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] должен инициировать разрешение ссылок, чтобы можно было отобразить подробные свойства для каждой ссылки в окне **Свойства** . В следующем списке описаны три типа ссылок и способы их разрешения.

- Ссылки на сборку:

   Система проекта вызывает целевой объект с известным именем `ResolveAssemblyReferences`. Этот целевой объект должен создать элементы с именем типа элемента `ReferencePath`. Каждый из этих элементов должен иметь спецификацию элемента (значение атрибута `Include` элемента), которая содержит полный путь к ссылке. Эти элементы должны иметь все метаданные, полученные от входных элементов, и, кроме того, следующие новые метаданные.

  - `CopyLocal`, указывающие, следует ли скопировать данную сборку в выходную папку, для чего надо присвоить ей значение "true" или "false".

  - `OriginalItemSpec`, содержащую исходную спецификацию элемента ссылки.

  - `ResolvedFrom`, для которого было задано значение "{TargetFrameworkDirectory}", если он был разрешен из каталога .NET Framework.

- Ссылки COM:

   Система проекта вызывает целевой объект с известным именем `ResolveCOMReferences`. Этот целевой объект должен создать элементы с именем типа элемента `ComReferenceWrappers`. Каждый из этих элементов должен иметь спецификацию элемента, которая содержит полный путь к ссылке взаимодействия для ссылки СОМ. Эти элементы должны иметь все метаданные, переданные от входных элементов, и, кроме того, новые метаданные с именем `CopyLocal`, указывающие, следует ли копировать данную сборку в выходную папку, с заданным значением "true" или "false".

- Машинные ссылки

   Система проекта вызывает целевой объект с известным именем `ResolveNativeReferences`. Этот целевой объект должен создать элементы с именем типа элемента `NativeReferenceFile`. Эти элементы должны иметь все метаданные, переданные от входных элементов, и, кроме того, новую порцию метаданных с именем `OriginalItemSpec`, содержащих спецификацию исходных элементов ссылки.

## <a name="performance-shortcuts"></a>Ярлыки производительности
 Если вы используете интегрированную среду разработки Visual Studio для запуска отладки (с помощью клавиши F5 или пункта меню **Отладка** > **Начать отладку**) или сборки проекта (например, **Сборка** > **Собрать решение**), для повышения производительности в процессе сборки будет использоваться быстрая проверка обновлений. В некоторых случаях, когда пользовательские построения создают файлы, которые в свою очередь также участвуют в построениях, быстрая проверка обновлений не может верно определить измененные файлы. В проектах, которые требуют более тщательных проверок обновлений, можно отключить быструю проверку, задав переменную среды `DISABLEFASTUPTODATECHECK=1`. Другой способ — задать ее в качестве свойства MSBuild в проекте или в файле, импортируемом в проект.

 Для обычной сборки в Visual Studio быстрая проверка обновлений не применяется, и сборка проекта будет выполняться, как если бы сборка была вызвана из командной строки.

## <a name="see-also"></a>См. также
- [Практическое руководство. Расширение процесса сборки Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Запуск сборки из интегрированной среды разработки](../msbuild/starting-a-build-from-within-the-ide.md)
- [Регистрация расширений платформы .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Элемент Property (MSBuild)](../msbuild/property-element-msbuild.md)
- [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Задача Csc](../msbuild/csc-task.md)
- [Задача Vbc](../msbuild/vbc-task.md)