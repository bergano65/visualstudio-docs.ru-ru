---
title: 'Как: создать. Vsct-файле | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-vsct-file"></a>Как: создать. Vsct-файла  
  
Существует несколько способов создания файла конфигурации (.vsct) на базе XML Visual Studio Command Table.  
  
-   Можно создать новый пакет VSPackage в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблона пакета.  
  
-   Компилятор конфигурации таблицы команд на основе XML, Vsct.exe, можно использовать для создания файла из существующего файла ctc.  
  
-   Vsct.exe можно использовать для создания vsct-файл из существующего файла cto.  
  
-   Можно вручную создать vsct-файл.  
  
 В этом разделе объясняется, как вручную создать vsct-файл.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Чтобы вручную создать vsct-файл  
  
1.  Запустите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  На **файл** последовательно выберите пункты **New**, а затем нажмите кнопку **файл**.  
  
3.  В **шаблоны** области, нажмите кнопку **XML-файл** и нажмите кнопку **откройте**.  
  
4.  На **представление** меню, нажмите кнопку **окно свойств** для отображения свойств XML-файла.  
  
5.  В **свойства** окно, нажмите кнопку обзора (...) для свойства схемы.  
  
6.  В списке XSD-схемы выберите схему vsct.xsd. Если он отсутствует в списке, нажмите кнопку **добавить** и найдите файл на локальный диск. Нажмите кнопку **ОК** по окончании.  
  
7.  В XML-файле введите `<CommandTable` и нажмите клавишу TAB. Закрыть тег, введя `>`.  
  
     Это создает базовый vsct-файл.  
  
8.  Заполнять элементы XML-файл, который требуется добавить, в соответствии с [VSCT схемы](../../extensibility/vsct-xml-schema-reference.md). Дополнительные сведения см. в разделе [Authoring. Файлы Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Практическое руководство. Создание файла VSCT на основе существующего файла CTC  
  
Вы можете создать файл VSTC на основе XML из существующего исходного CTC-файла таблицы команд. Таким образом, можно воспользоваться преимуществами нового основанный на XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] формата компилятора таблицы (VSCT) команд.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC  
  
1.  Получите копию языка Perl.  
  
2.  Получите копию скрипта ConvertCTCToVSCT.pl, Perl, обычно находится в  *\<путь установки Visual Studio SDK >*папки \VisualStudioIntegration\Tools\bin.  
  
3.  Получите копию исходного файла CTC, который нужно преобразовать.  
  
4.  Поместите файлы в один каталог.  
  
5.  В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] окне командной строки, перейдите в каталог.  
  
6.  Тип  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Здесь PkgCmd.ctc — это имя файла CTC, а PkgCmd.vsct — имя файла VSCT, который нужно создать.  
  
     Будет создан исходный VSCT-файл таблицы команд XML. Этот файл можно скомпилировать с помощью Vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
    > [!NOTE]
    >  Чтобы повысить удобочитаемость файла VSCT, можно переформатировать комментарии XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Практическое руководство. Создание файла VSCT на основе существующего файла CTO  
  
Вы можете создать файл VSTC на основе XML из существующего двоичного CTO-файла. Это позволяет воспользоваться преимуществами нового формата компилятора таблицы команд. Этот процесс работает, даже если файл CTO был скомпилирован из файла CTC. Файл VSCT можно изменить и скомпилировать в другой файл CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Создание файла VSCT на основе файла CTO  
  
1.  Получите копии файла CTO и соответствующего файла CTSYM.  
  
2.  Поместите файлы в тот же каталог, что и компилятор vsct.exe.  
  
3.  В командной строке Visual Studio перейдите в каталог, содержащий файлы CTO и CTSYM.  
  
4.  Тип **vsct.exe** *ctofilename *** .cto** * vsctfilename***.vsct -S***symfilename ***.ctsym**.  
  
     `ctofilename` Имя файла cto `vsctfilename` имя файла vsct, который нужно создать, и `symfilename` имя файла ctsym.  
  
     В результате этого процесса будет создан файл компилятора таблицы команд XML. Этот файл можно изменить и скомпилировать с помощью vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Просто добавив vsct-файл в проект не приводит к его компиляции. Его необходимо включить в процесс построения.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Чтобы добавить vsct-файл для компиляции проекта  
  
1.  Откройте файл проекта в редакторе. При загрузке проекта сначала его необходимо выгрузить.  
  
2.  Добавить [элемент ItemGroup](../../msbuild/itemgroup-element-msbuild.md) , содержит элемент VSCTCompile, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Элемент ResourceName должно всегда быть присвоено `Menus.ctmenu`.  
  
3.  Если проект содержит файл RESX, добавьте EmbeddedResource элементом, который содержит элемент MergeWithCTO, как показано в следующем примере.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Эта разметка должна находиться внутри элемент ItemGroup, содержащий внедренные ресурсы.  
  
4.  Открыть файл пакета, обычно с именем *ProjectName*Package.cs или *ProjectName*Package.vb в редакторе.  
  
5.  Добавление атрибута ProvideMenuResource класс пакета, как показано в следующем примере.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Значение первого параметра должно соответствовать значение атрибута ResourceName, заданных в файле проекта.  
  
## <a name="see-also"></a>См. также  
 [Разработка. Файлы Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)