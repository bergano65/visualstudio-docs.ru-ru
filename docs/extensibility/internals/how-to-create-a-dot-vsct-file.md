---
title: Как выполнить Создать. Файл Vsct | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b7c050022f129369962c572cbb5a60a27cca547
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979690"
---
# <a name="how-to-create-a-vsct-file"></a>Как выполнить Создание файла vsct  
  
Существует несколько способов для создания конфигурации таблицы команд Visual Studio на основе XML (*.vsct*) файла.  
  
- Можно создать новый пакет VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблона пакета.  
  
- Можно использовать конфигурации компилятора таблицы команд на основе XML, *Vsct.exe*, чтобы создать файл из существующего *.ctc* файла.  
  
- Можно использовать *Vsct.exe* для создания *.vsct* файл из существующего *.cto* файла.  
  
- Можно вручную создать новый *.vsct* файла.  
  
  В этой статье объясняется, как вручную создать новый *.vsct* файла.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Чтобы вручную создать новый vsct-файл  
  
1. Запустите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2. На **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **файл**.  
  
3. В **шаблоны** панели щелкните **XML-файл** и нажмите кнопку **откройте**.  
  
4. На **представление** меню, щелкните **свойства** для отображения свойств XML-файла.  
  
5. В **свойства** окно, нажмите кнопку **Обзор** кнопку **схемы** свойство.  
  
6. В списке XSD-схемы, выберите *vsct.xsd* схемы. Если он отсутствует в списке, нажмите кнопку **добавить** и затем найдите файл на локальном диске. Нажмите кнопку **ОК** при завершении работы.  
  
7. В XML-файле введите *< CommandTable* и нажмите клавишу **вкладке**. Закрыть тег, введя *>*.  
  
    Это действие создает базовое *.vsct* файла.  
  
8. Заполнение в элементах XML-файла, который вы хотите добавить, в соответствии с [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [создать vsct-файлы](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Как выполнить Создание файла .vsct из существующего файла ctc  
  
Можно создать на базе XML *.vsct* файл из существующей таблицы команды *.ctc* исходный файл. Таким образом можно воспользоваться новым форматом компилятора таблицы команд [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе XML (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC  
  
1. Получите копию языка Perl.  
  
2. Получить копию и скрипт Perl *ConvertCTCToVSCT.pl*, который обычно находится в  *\<путь установки пакета SDK для Visual Studio > \VisualStudioIntegration\Tools\bin* папки.  
  
3. Получить копию *.ctc* исходного файла, который требуется преобразовать.  
  
4. Поместите файлы в один каталог.  
  
5. В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] окне командной строки, перейдите в каталог.  
  
6. Тип  
  
   ```  
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
   ```  
  
    где *pkgcmd.ctc —* имя *.ctc* файл и *PkgCmd.vsct* имя *.vsct* файл, который вы хотите создать.  
  
    Это действие создает новую *.vsct* файл источника таблицы команд XML. Этот файл можно скомпилировать с помощью *Vsct.exe*, компилятора VSCT, как вы и другие *.vsct* файла.  
  
   > [!NOTE]
   >  Можно улучшить читаемость *.vsct* файла переформатировать комментарии XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Как выполнить Создание файла vsct на основе существующего файла cto  
  
Можно создать на базе XML *.vsct* файл из существующего двоичного файла *.cto* файла. Это позволяет воспользоваться преимуществами нового формата компилятора таблицы команд. Этот процесс работает даже если *.cto* файл составлен из *.ctc* файла. Можно изменить и скомпилировать *.vsct* файл в другой файл cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Создание файла VSCT на основе файла CTO  
  
1.  Получите копии *.cto* файла и его соответствующее *.ctsym* файла.  
  
2.  Поместите файлы в той же папке, что *vsct.exe* компилятора.  
  
3.  В командной строке Visual Studio, перейдите в каталог, содержащий *.cto* и *.ctsym* файлов.  
  
4.  Тип  

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     где \<ctofilename\> имя *.cto* файл, \<vsctfilename\> имя *.vsct* файл вы хотите создать, а также \<symfilename\> имя *.ctsym* файла.  
  
     Этот процесс создает новую *.vsct* файл компилятора таблицы команд XML. Можно изменить и скомпилировать его с *vsct.exe*, компилятора vsct, как вы и другие *.vsct* файла.  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Простое добавление *.vsct* файл в проект не приводит к его компиляции. Его необходимо включить в процессе построения.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Чтобы добавить vsct-файл для компиляции проекта  
  
1.  Откройте файл проекта в редакторе. Если проект загружен, сначала его необходимо выгрузить.  
  
2.  Добавить [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) , содержащий `VSCTCompile` элемента, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     `ResourceName` Элемент всегда должен иметь значение `Menus.ctmenu`.  
  
3.  Если проект содержит *.resx* добавьте `EmbeddedResource` элемент, содержащий `MergeWithCTO` элемента, как показано в следующем примере:  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Эта разметка должна находиться внутри `ItemGroup` элемент, содержащий внедренные ресурсы.  
  
4.  Открыть файл пакета, обычно с именем  *\<имя_проекта\>Package.cs* или  *\<имя_проекта\>Package.vb*, в редакторе.  
  
5.  Добавление `ProvideMenuResource` атрибута к классу пакета, как показано в следующем примере.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Значение первого параметра должно соответствовать значению из `ResourceName` атрибутом, определенным в файле проекта.  
  
## <a name="see-also"></a>См. также  
 [Автор vsct-файлы](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio командные файлы table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)