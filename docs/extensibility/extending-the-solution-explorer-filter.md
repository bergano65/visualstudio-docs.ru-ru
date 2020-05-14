---
title: Расширение фильтра для исследователей решений (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711574"
---
# <a name="extend-the-solution-explorer-filter"></a>Расширить фильтр Solution Explorer
Вы можете расширить функциональность фильтра **Solution Explorer,** чтобы показать или скрыть различные файлы. Например, можно создать фильтр, который отображает только фабричные файлы класса C в **Solution Explorer,** как это показывает пошаговый шаг.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-package-project"></a>Создание проекта пакета Visual Studio

1. Создайте проект VSIX под названием `FileFilter`. Добавьте пользовательский шаблон элемента командпод названием **FileFilter.** Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Добавить ссылку на `System.ComponentModel.Composition` и `Microsoft.VisualStudio.Utilities`.

3. Сделайте так, чтобы команда меню отображалась на панели инструментов **Solution Explorer.** Откройте файл *FileFilterPackage.vsct.*

4. Измените `<Button>` блок на следующее:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Обновление файла манифеста

1. В файле *source.extension.vsixmanifest* добавьте актив, который является компонентом MEF.

2. На вкладке **«Активы»** выберите **новую** кнопку.

3. В поле **Type** выберите **Microsoft.VisualStudio.MefComponent**.

4. В поле **Source** выберите **проект в текущем решении.**

5. В поле **проекта** выберите **FileFilter,** а затем выберите кнопку **OK.**

### <a name="add-the-filter-code"></a>Добавить код фильтра

1. Добавьте некоторые GUID *в* FileFilterPackageGuids.cs файл:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Добавьте файл класса в проект FileFilter под названием *FileNameFilter.cs.*

3. Замените пустое пространство имен и пустой класс кодом ниже.

     Метод `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` берет коллекцию, которая содержит корень`rootItems`решения ( ) и возвращает коллекцию элементов, которые будут включены в фильтр.

     Метод `ShouldIncludeInFilter` фильтрует элементы в иерархии **Solution Explorer** в зависимости от состояния, которое вы указываете.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. В *FileFilter.cs*удалите код размещения и обработки команд из конструктора FileFilter. Результат должен выглядеть следующим образом:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Удалите `ShowMessageBox()` метод, а также.

5. В *FileFilterPackage.cs,* замените `Initialize()` код в методе следующим:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Тестирование кода

1. Постройте и запустите проект. Откроется второй экземпляр Visual Studio. Это называется экспериментальным экземпляром.

2. В экспериментальном экземпляре Visual Studio откройте проект c-.

3. Ищите кнопку, добавленную на панели инструментов **Solution Explorer.** Это должна быть четвертая кнопка слева.

4. При нажатии кнопки все файлы должны быть отфильтрованы, и вы должны увидеть, что **все элементы были отфильтрованы из представления.** в **исследователе решения**.
