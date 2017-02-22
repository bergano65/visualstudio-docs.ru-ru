---
title: "Практическое руководство: создание. Файл Vsct | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-файлы, создание"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: создание. Файл Vsct
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Существует несколько способов создания файла конфигурации \(.vsct\) на основе XML таблицы команд Visual Studio.  
  
-   Можно создать новый пакет VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблона пакета.  
  
-   Компилятор конфигурации таблицы команд на основе XML, Vsct.exe, можно использовать для создания файла из существующего файла .ctc.  
  
-   Vsct.exe можно использовать для создания файла .vsct из существующего файла .cto.  
  
-   Можно вручную создать новый файл .vsct.  
  
 В этом разделе объясняется, как вручную создать новый файл .vsct.  
  
### Чтобы вручную создать новый файл .vsct  
  
1.  Запустите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  На **файл** наведите указатель мыши на **New**, а затем нажмите кнопку **файл**.  
  
3.  В **шаблоны** панели, щелкните **XML\-файл** и нажмите кнопку **Откройте**.  
  
4.  На **представление** меню, щелкните **окно свойств** для отображения свойств XML\-файла.  
  
5.  В **Свойства** окно, нажмите кнопку обзора \(...\) Кнопка для свойства схемы.  
  
6.  В списке XSD\-схемы выберите схему vsct.xsd. Если нет в списке, нажмите кнопку **Добавить** и найдите файл на локальный диск. Щелкните **ОК** по окончании.  
  
7.  В XML\-файл, введите `<CommandTable` и нажмите клавишу TAB. Закрыть тег, введя `>`.  
  
     Будет создан файл основные .vsct.  
  
8.  Заполнить элементы XML\-файл, который требуется добавить, в соответствии с [схемы VSCT](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [Разработка. Vsct\-файлы](../../extensibility/internals/authoring-dot-vsct-files.md).  
  
## Компиляция кода  
 Добавления в проект файла .vsct не вызывает его компиляции. Его необходимо включить в процесс построения.  
  
### Чтобы добавить файл .vsct для компиляции проекта  
  
1.  Откройте файл проекта в редакторе. Если проект загружен, необходимо его выгрузить сначала.  
  
2.  Добавить [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) содержит элемент VSCTCompile, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Элемент ResourceName всегда должно быть присвоено `Menus.ctmenu`.  
  
3.  Если проект содержит файл .resx, добавьте EmbeddedResource элемента, который содержит элемент MergeWithCTO, как показано в следующем примере.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Эта разметка должна находиться внутри ItemGroup\-элемент, содержащий внедренные ресурсы.  
  
4.  Открыть файл пакета, обычно называется *ProjectName*Package.cs или *ProjectName*Package.vb в редакторе.  
  
5.  Добавьте атрибут ProvideMenuResource в класс пакета, как показано в следующем примере.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Значение первого параметра должно соответствовать значение атрибута ResourceName, заданных в файле проекта.  
  
## См. также  
 [Разработка. Vsct\-файлы](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Практическое руководство. Создание файла VSCT на основе существующего файла CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Практическое руководство. Создание файла VSCT на основе существующего файла CTO](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)