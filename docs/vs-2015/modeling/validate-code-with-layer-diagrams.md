---
title: Validate code with layer diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, validating
- validation, layer diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, layer diagrams
- MSBuild, validating code
ms.assetid: 70cbe55d-4b33-4355-b0a7-88c770a6f75c
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 596711c5c59738d5356437bb761e80caeddfbd6b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301357"
---
# <a name="validate-code-with-layer-diagrams"></a>Проверка кода по схемам слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы убедиться в том, что код не конфликтует со структурой, проверьте его с помощью схем слоев в Visual Studio. Это может помочь:

- Найти конфликты между зависимостями в коде и зависимостями на схеме слоев.

- Найти зависимости, на которые могут повлиять предложенные изменения.

   Например, можно изменить схему слоев для отображения потенциальных изменений архитектуры, а затем проверить код, чтобы увидеть зависимости, на которые повлияли эти изменения.

- Выполнить рефакторинг или миграцию кода в другую структуру.

   Найти код или зависимости, с которыми потребуется выполнить определенные действия даже после перемещения кода в другую архитектуру.

  **Requirements**

- Visual Studio

- Visual Studio на сервере Team Foundation Build для проверки кода автоматически с помощью Team Foundation Build

- Решение, включающее проект моделирования со схемой слоев. Эта схема слоев должна быть связана с артефактами в проектах Visual C# .NET или Visual Basic .NET, которые необходимо проверить. See [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md).

  Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

  Можно проверить код вручную из открытой схемы слоев в Visual Studio или из командной строки. Также код можно проверить автоматически при выполнении локальных сборок или Team Foundation Build. See [Channel 9 Video: Design and validate your architecture using layer diagrams](https://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Если необходимо выполнить проверку слоев в Team Foundation Build, следует также установить ту же версию Visual Studio на сервере сборки.

- [See if an item supports validation](#SupportsValidation)

- [Include other .NET assemblies and projects for validation](#IncludeReferences)

- [Validate code manually](#ValidateManually)

- [Validate code automatically](#ValidateAuto)

- [Troubleshoot layer validation issues](#TroubleshootingValidation)

- [Understand and resolve layer validation errors](#UnderstandingValidationErrors)

## <a name="SupportsValidation"></a> See if an item supports validation
 Можно связать слои с веб-сайтами, документами Office, обычными текстовыми файлами и файлами в проектах, которые являются общими для нескольких приложений, но они не войдут в процесс проверки. Ошибки проверки для ссылок на проекты или сборки, связанные с отдельными слоями, отображаются только в том случае, если между этими слоями отображаются зависимости. Эти ссылки считаются зависимостями, только если используются в коде.

1. On the layer diagram, select one or more layers, right-click your selection, and then click **View Links**.

2. In **Layer Explorer**, look at the **Supports Validation** column. Если значение равно false, элемент не поддерживает проверку.

## <a name="IncludeReferences"></a> Include other .NET assemblies and projects for validation
 When you drag items to the layer diagram, references to the corresponding .NET assemblies or projects are added automatically to the **Layer References** folder in the modeling project. Эта папка содержит ссылки на сборки и проекты, которые анализируются во время проверки. Также можно добавить другие сборки и проекты .NET для проверки, не перетаскивая их на схему слоев вручную.

1. In **Solution Explorer**, right-click the modeling project or the **Layer References** folder, and then click **Add Reference**.

2. In the **Add Reference** dialog box, select the assemblies or projects, and then click **OK**.

## <a name="ValidateManually"></a> Validate code manually
 If you have an open layer diagram that is linked to solution items, you can run the **Validate** shortcut command from the diagram. You can also use the command prompt to run the **msbuild** command with the **/p:ValidateArchitecture** custom property set to **True**. Например, при внесении изменений в код регулярно выполняйте проверку слоев, чтобы заранее обнаруживать конфликты зависимостей.

#### <a name="to-validate-code-from-an-open-layer-diagram"></a>Проверка кода из открытой схемы слоев

1. Right-click the diagram surface, and then click **Validate Architecture**.

    > [!NOTE]
    > By default, the **Build Action** property on the layer diagram (.layerdiagram) file is set to **Validate** so that the diagram is included in the validation process.

     The **Error List** window reports any errors that occur. For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

2. To view the source of each error, double-click the error in the **Error List** window.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] может вместо источника ошибки показывать карту кода. Это происходит, если код имеет зависимость в сборке, не заданной схемой слоев, либо в коде отсутствует зависимость, заданная схемой слоев. Просмотрите карту кода или код, чтобы определить, должна ли существовать зависимость. For more information about code maps, see [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

3. To manage errors, see [Manage validation errors](#ManageErrors).

#### <a name="to-validate-code-at-the-command-prompt"></a>Проверка кода в командной строке

1. Откройте командную строку [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Выберите один из следующих вариантов.

   - Чтобы проверить код на соответствие конкретному проекту моделирования в решении, запустите [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] со следующим пользовательским свойством.

     ```
     msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
     ```

     - или

       Откройте папку, в которой находится файл проекта моделирования (MODELPROJ-файл) и схема слоев, и запустите [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] со следующим пользовательским свойством.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

   - Чтобы проверить код на соответствие всем проектам моделирования в решении, запустите [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] со следующим пользовательским свойством.

     ```
     msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
     ```

     - или

       Откройте папку решения, в которой должен находиться проект моделирования со схемой слоев, и запустите [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] со следующим пользовательским свойством.

     ```
     msbuild /p:ValidateArchitecture=true
     ```

     Отобразятся любые возникающие ошибки. For more information about [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], see [MSBuild](../msbuild/msbuild.md) and [MSBuild Task](../msbuild/msbuild-task.md).

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

### <a name="ManageErrors"></a> Manage validation errors
 В процессе разработки может понадобиться подавить некоторые конфликты, выявленные в ходе проверки. Например, можно подавлять ошибки, над которыми уже ведется работа, а также ошибки, не имеющие отношения к конкретному сценарию. При подавлении ошибки рекомендуется фиксировать рабочий элемент в журнале в [!INCLUDE[esprfound](../includes/esprfound-md.md)].

> [!WARNING]
> Вы должны быть уже подключены к управлению исходным кодом (SCC) TFS для создания рабочего элемента или связи с ним. При попытке открыть соединение с другим SCC TFS Visual Studio автоматически закрывает текущее решение. Убедитесь, что вы уже подключены соответствующему SCC, перед попыткой создания рабочего элемента или связи с ним. В последних выпусках Visual Studio команды меню недоступны, если вы не подключены к SCC.

##### <a name="to-create-a-work-item-for-a-validation-error"></a>Создание рабочего элемента для ошибки проверки

- In the **Error List** window, right-click the error, point to **Create Work Item**, and then click the type of work item that you want to create.

  Use these tasks to manage validation errors in the **Error List** window:

|**Задача**|**Follow these steps**|
|------------|----------------------------|
|Подавить выбранные ошибки во время проверки|Right-click the one or multiple selected errors, point to **Manage Validation Errors**, and then click **Suppress Errors**.<br /><br /> Отобразятся подавленные ошибки с форматированием в виде зачеркивания. При выполнении проверки в следующий раз эти ошибки отображаться не будут.<br /><br /> Подавленные ошибки отслеживаются в SUPPRESSIONS-файле, относящемся к соответствующему файлу схемы слоев.|
|Остановить подавление выбранных ошибок|Right-click the selected suppressed error or errors, point to **Manage Validation Errors**, and then click **Stop Suppressing Errors**.<br /><br /> При выполнении проверки в следующий раз выбранные подавленные ошибки будут отображаться.|
|Restore all suppressed errors in the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Show All Suppressed Errors**.|
|Hide all suppressed errors from the **Error List** window|Right-click anywhere in the **Error List** window, point to **Manage Validation Errors**, and then click **Hide All Suppressed Errors**.|

## <a name="ValidateAuto"></a> Validate code automatically
 Проверку слоев можно выполнять при каждом выполнении локальной сборки. Если команда использует Team Foundation Build, можно выполнить проверку слоев с записью с проверкой изменений, которые можно задать путем создания пользовательской задачи MSBuild, и использовать отчеты по сборке для сбора ошибок проверки. To create gated check-in builds, see [Use a gated check-in build process to validate changes](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec).

#### <a name="to-validate-code-automatically-during-a-local-build"></a>Автоматическая проверка кода во время локальной сборки

- Откройте файл проекта моделирования (.modelproj) в текстовом редакторе и включите следующее свойство.

```
<ValidateArchitecture>true</ValidateArchitecture>
```

 \- или -

1. In **Solution Explorer**, right-click the modeling project that contains the layer diagram or diagrams, and then click **Properties**.

2. In the **Properties** window, set the modeling project's **Validate Architecture** property to **True**.

    Это позволяет включить проект моделирования в процесс проверки.

3. In **Solution Explorer**, click the layer diagram (.layerdiagram) file that you want to use for validation.

4. In the **Properties** window, make sure that the diagram's **Build Action** property is set to **Validate**.

    Это позволяет включить схему слоев в процесс проверки.

   To manage errors in the Error List window, see [Manage Validation Errors](#ManageErrors).

#### <a name="to-validate-code-automatically-during-a-team-foundation-build"></a>Автоматическая проверка кода во время выполнения Team Foundation Build

1. In **Team Explorer**, double-click the build definition, and then click **Process**.

2. Under **Build process parameters**, expand **Compilation**, and type the following in the **MSBuild Arguments** parameter:

    `/p:ValidateArchitecture=true`

   For more information about validation errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors). Дополнительные сведения о [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] см. в разделах:

- [Сборка приложения](/azure/devops/pipelines/index)

- [Use the Default Template for your build process](https://msdn.microsoft.com/library/43930b12-c21b-4599-a980-2995e3d16e31)

- [Modify a Legacy Build that is Based on UpgradeTemplate.xaml](https://msdn.microsoft.com/library/ee1a8259-1dd1-4a10-9563-66c5446ef41c)

- [Настройка шаблона процесса сборки](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

- [Monitor Progress of a Running Build](https://msdn.microsoft.com/library/e51e3bad-2d1d-4b7b-bfcc-c43439c6c8ef)

## <a name="TroubleshootingValidation"></a> Troubleshoot layer validation issues
 Следующая таблица описывает проблемы проверки слоев и способы их устранения. Эти проблемы отличаются от ошибок, возникающих из-за несоответствия между кодом и структурой. For more information about these errors, see [Understand and resolve layer validation errors](#UnderstandingValidationErrors).

|**Проблема**|**Possible Cause**|**Решение**|
|---------------|------------------------|--------------------|
|Ошибки проверки не возникают так, как это ожидается.|Проверка не работает на схемах слоев, которые скопированы из других схем слоев в обозревателе решений и находятся в том же проекте моделирования. Скопированные таким образом схемы слоев содержат те же ссылки, что и исходная схема слоев.|Добавьте новую схему слоев в проект моделирования.<br /><br /> Скопируйте элементы из исходной схемы слоев в новую схему.|

## <a name="UnderstandingValidationErrors"></a> Understanding and Resolving Layer Validation Errors
 При проверке кода с помощью схемы слоев будут происходить ошибки проверки, если код конфликтует со структурой. Например, ошибки проверки могут происходить по следующим причинам:

- Артефакт назначен неправильному слою. В этом случае следует переместить артефакт.

- Способ использования артефактом (например, классом) другого класса конфликтует с имеющейся архитектурой. В этом случае необходимо выполнить рефакторинг кода, чтобы устранить зависимость.

  Для устранения этих ошибок следует обновлять код до тех пор, пока в процессе проверки не перестанут происходить ошибки. Эту процедуру можно выполнить методом итераций.

  В следующем разделе описывается синтаксис, используемый в этих ошибках, объясняется значение этих ошибок и предлагаются пути решения или управления ими.

|**Синтаксис**|**Описание**|
|----------------|---------------------|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* is an artifact that is associated with a layer on the layer diagram.<br /><br /> *ArtifactTypeN* is the type of *ArtifactN*, such as a **Class** or **Method**, for example:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Имя пространства имен.|
|*LayerNameN*|Название слоя на диаграмме слоев.|
|*DependencyType*|The type of dependency relationship between *Artifact1* and *Artifact2*. For example, *Artifact1* has a **Calls** relationship with *Artifact2*.|

|**Error Syntax**|**Error Description**|
|----------------------|---------------------------|
|AV0001: Invalid Dependency: *Artifact1*(*ArtifactType1*) --> *Artifact2*(*ArtifactType2*)<br /><br /> Layers: *LayerName1*, *LayerName2* &#124; Dependencies: *DependencyType*|*Artifact1* in *LayerName1* should not have a dependency on *Artifact2* in *LayerName2* because *LayerName1* does not have a direct dependency on *LayerName2*.|
|AV1001: Invalid Namespace: *Artifact*<br /><br /> Layer: *LayerName* &#124; Required Namespace: *NamespaceName1* &#124; Current Namespace: *NamespaceName2*|*LayerName* requires that its associated artifacts must belong to *NamespaceName1*. *Artifact* is in *NamespaceName2*, not *NamespaceName1*.|
|AV1002: Depends on Forbidden Namespace: *Artifact1*(*ArtifactType1*) &#124; *Artifact2*(*ArtifactType2*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName* &#124; Dependencies: *DependencyType*|*LayerName* requires that its associated artifacts must not depend on *NamespaceName*. *Artifact1* cannot depend on *Artifact2* because *Artifact2* is in *NamespaceName*.|
|AV1003: In Forbidden Namespace: *Artifact*(*ArtifactType*)<br /><br /> Layer: *LayerName* &#124; Forbidden Namespace: *NamespaceName*|*LayerName* requires that its associated artifacts cannot belong to *NamespaceName*. *Artifact* belongs to *NamespaceName*.|
|AV3001: Missing Link: Layer '*LayerName*' links to '*Artifact*' which cannot be found. Отсутствует ссылка на сборку?|*LayerName* links to an artifact that cannot be found. Например, связь с классом может отсутствовать из-за отсутствия в проекте моделирования ссылки на сборку, содержащую этот класс.|
|AV9001: при проверке архитектуры обнаружены внутренние ошибки. Результат может быть неполным. Для получения дополнительных сведений см. подробный журнал событий построения или окно вывода.|Для получения дополнительных сведений см. журнал событий сборки или окно вывода.|

## <a name="security"></a>Безопасность

## <a name="see-also"></a>См. также раздел
 [Проверка системы в ходе разработки](../modeling/validate-your-system-during-development.md)
