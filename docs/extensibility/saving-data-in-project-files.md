---
title: Сохранение данных в файлах проекта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701345"
---
# <a name="save-data-in-project-files"></a>Сохранение данных в файлах проекта
Подтип проекта может сохранять и извлекать данные, специфичные для подтипов, в файле проекта. Рамочная программа управляемого пакета (MPF) предоставляет два интерфейса для выполнения этой задачи:

- Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> позволяет получить доступ к значениям свойств из раздела **MSBuild** файла проекта. Методы, предоставляемые <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> может быть вызван любым пользователем, когда пользователь должен загрузить или сохранить сборку соответствующих данных.

- Используется <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения несвязанных данных в свободной форме XML. Методы, предоставляемые, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вызываются [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] всякий раз, когда необходимо сохранять не связанные с ними данные в файле проекта.

  Для получения дополнительной информации о том, как [Persist data in the MSBuild project file](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)упорствовать в сборке и не связанных с ними данных, см.

## <a name="save-and-retrieve-build-related-data"></a>Сохранение и извлечение данных, связанных с сборкой

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Сохранение связанных с сборкой данных в файле проекта

- Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> метод, чтобы сохранить полный путь файла проекта.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Извлечение данных, связанных с сборкой из файла проекта

- Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> метод для получения полного пути файла проекта.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Сохранение и извлечение непостровных данных, связанных с сборкой

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Сохранение непостровных данных в файле проекта

1. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> метода, чтобы определить, изменялся ли фрагмент XML с момента его последнего сохранения в текущем файле.

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

2. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> метода сохранения данных XML в файле проекта.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Для извлечения непостровных данных в файле проекта

1. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> метода инициализации свойств расширения проекта и других независях от сборки данных. Этот метод вызывается, если в файле проекта нет данных конфигурации XML.

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

2. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> метода загрузки данных XML из файла проекта.

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
> Все примеры кода, приведенные в этой теме, являются частями более крупного примера в [образцах VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>См. также
- [Сохраняющиеся данные в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
