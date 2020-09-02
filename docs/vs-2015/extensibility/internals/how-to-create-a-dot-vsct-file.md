---
title: Как создать. Файл vsct | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158351"
---
# <a name="how-to-create-a-vsct-file"></a>Практическое руководство. Создание VSCT-файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Существует несколько способов создания файла конфигурации таблицы команд Visual Studio (vsct) на основе XML.  
  
- В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] шаблоне пакета можно создать новый пакет VSPackage.  
  
- Для создания файла из существующего CTC-файла можно использовать компилятор конфигурации таблицы команд на основе XML, Vsct.exe.  
  
- Vsct.exe можно использовать для создания файла vsct из существующего CTO-файла.  
  
- Новый vsct-файл можно создать вручную.  
  
  В этом разделе объясняется, как вручную создать новый vsct-файл.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Создание нового vsct-файла вручную  
  
1. Запустите среду [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. В меню **Файл** укажите пункт **Создать**, а затем выберите пункт **Файл**.  
  
3. В области **шаблоны** выберите **XML-файл** и нажмите кнопку **Открыть**.  
  
4. В меню **вид** выберите пункт **окно свойств** , чтобы отобразить свойства XML-файла.  
  
5. В окне **Свойства** нажмите кнопку обзора (...) в свойстве схемы.  
  
6. В списке схем XSD выберите схему vsct. xsd. Если он отсутствует в списке, нажмите кнопку **Добавить** , а затем найдите файл на локальном диске. По завершении нажмите кнопку **ОК** .  
  
7. В XML-файле введите `<CommandTable` и нажмите клавишу TAB. Закройте тег, введя `>` .  
  
     При этом создается файл Basic. vsct.  
  
8. Заполните элементы XML-файла, который требуется добавить, в соответствии со [схемой VSCT](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [Разработка. Файлы vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Простое добавление файла vsct в проект не приводит к его компиляции. Его необходимо включить в процесс сборки.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Добавление файла. vsct в компиляцию проекта  
  
1. Откройте файл проекта в редакторе. Если проект загружен, его необходимо сначала выгрузить.  
  
2. Добавьте [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) , содержащий элемент вскткомпиле, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Элемент ResourceName всегда должен иметь значение `Menus.ctmenu` .  
  
3. Если проект содержит RESX-файл, добавьте элемент EmbeddedResource, содержащий элемент Мержевискто, как показано в следующем примере.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Эта разметка должна находиться внутри элемента ItemGroup, который содержит внедренные ресурсы.  
  
4. Откройте файл пакета, обычно именуемый *projectname*Package.cs или *имяПроекта*Package. vb, в редакторе.  
  
5. Добавьте атрибут Провидеменуресаурце в класс Package, как показано в следующем примере.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Первое значение параметра должно соответствовать значению атрибута ResourceName, определенного в файле проекта.  
  
## <a name="see-also"></a>См. также:  
 [Работы. Файлы vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Командная таблица Visual Studio (. Vsct) файлы](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Как создать. Vsct файл из существующего. Файл CTC](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Как создать. Vsct файл из существующего. Файл CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
