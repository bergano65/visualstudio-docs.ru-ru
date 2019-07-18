---
title: Практическое руководство. Создать. Файл Vsct | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158351"
---
# <a name="how-to-create-a-vsct-file"></a>Практическое руководство. Создание VSCT-файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Существует несколько способов создания файла конфигурации (.vsct) на базе XML Visual Studio Command Table.  
  
- Можно создать новый пакет VSPackage в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] шаблона пакета.  
  
- Компилятор конфигурации таблицы команд на основе XML, Vsct.exe, можно использовать для создания файла из существующего файла ctc.  
  
- Чтобы создать vsct-файл из существующего файла cto, можно использовать Vsct.exe.  
  
- Можно вручную создать новый файл .vsct.  
  
  В этом разделе объясняется, как вручную создать новый файл .vsct.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Чтобы вручную создать новый vsct-файл  
  
1. Запустите [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. На **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **файл**.  
  
3. В **шаблоны** панели щелкните **XML-файл** и нажмите кнопку **откройте**.  
  
4. На **представление** меню, щелкните **окно "Свойства"** для отображения свойств XML-файла.  
  
5. В **свойства** окно, нажмите кнопку обзора (...) в свойстве «схемы».  
  
6. В списке XSD-схемы выберите схему vsct.xsd. Если он отсутствует в списке, нажмите кнопку **добавить** и затем найдите файл на локальном диске. Нажмите кнопку **ОК** при завершении работы.  
  
7. В XML-файле введите `<CommandTable` и нажмите клавишу TAB. Закрыть тег, введя `>`.  
  
     Это создает базовый vsct-файл.  
  
8. Заполнение в элементах XML-файла, который вы хотите добавить, в соответствии с [VSCT схемы](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [Создание и настройка. Файлы Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Простое добавление vsct-файл проекта не приводит к его компиляции. Его необходимо включить в процессе построения.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Чтобы добавить vsct-файл для компиляции проекта  
  
1. Откройте файл проекта в редакторе. Если проект загружен, сначала его необходимо выгрузить.  
  
2. Добавить [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) , содержащий элемент VSCTCompile, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Элемент ResourceName всегда должно быть присвоено `Menus.ctmenu`.  
  
3. Если проект содержит файл RESX, добавьте элемент EmbeddedResource, содержащий элемент MergeWithCTO, как показано в следующем примере.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Эта разметка должна находиться внутри элемент ItemGroup, содержащий внедренные ресурсы.  
  
4. Открыть файл пакета, обычно с именем *имя_проекта*Package.cs или *имя_проекта*Package.vb в редакторе.  
  
5. Добавьте атрибут ProvideMenuResource к классу пакета, как показано в следующем примере.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Значение первого параметра должно соответствовать значение атрибута ResourceName, заданных в файле проекта.  
  
## <a name="see-also"></a>См. также  
 [Разработка. Файлы Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Практическое руководство. Создать. Vsct-файл из существующего. Файла ctc](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Практическое руководство. Создать. Vsct-файл из существующего. Файл Технический директор](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
