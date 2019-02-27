---
title: Сохранение данных в файлах проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cd79925023a32a68ff4a9ac5f86f85d9c6798bf
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843598"
---
# <a name="save-data-in-project-files"></a>Сохранить данные в файлах проектов
Подтип проекта можно сохранять и извлекать подтипа данных в файле проекта. Managed Package Framework (MPF) предоставляет два интерфейса для выполнения этой задачи:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Интерфейс обеспечивает доступ значений свойств из **MSBuild** раздел файла проекта. Методы, предоставляемые <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> может вызываться любым пользователем, каждый раз, когда необходимо взвесить, чтобы загрузить или сохранить связанные данные сборок.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Используется для хранения без построения взаимосвязанные данные в XML произвольной формы. Методы, предоставляемые <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> вызываются [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] всякий раз, когда [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] требуется сохранить связанные данные без построения в файле проекта.

  Дополнительные сведения о том, как для сохранения сборки и связанные данные без построения см. в разделе [сохранять данные в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Сохранение и извлечение сборки связанных данных

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Чтобы сохранить построения связанные данные в файле проекта

-   Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод, чтобы сохранить полный путь файла проекта.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Для получения сборки связанные данные из файла проекта

-   Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> метод для извлечения полный путь файла проекта.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Сохранять и извлекать связанные данные без построения

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Чтобы сохранить без построения связанные данные в файле проекта

1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> метод, чтобы определить, изменился ли фрагмент XML с момента его последнего сохранения в свой текущий файл.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> метод, чтобы сохранить данные XML в файле проекта.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Для получения взаимосвязанных данных без построения в файле проекта

1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> метод для инициализации свойства расширения проекта и другие независимые от построения данные. Этот метод вызывается в том случае, если отсутствуют данные конфигурации XML в файле проекта.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> метод для загрузки XML-данные из файла проекта.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
>  Все примеры кода, приведенные в этом разделе являются частью более крупного примера в [примеры VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>См. также
- [Сохранять данные в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)