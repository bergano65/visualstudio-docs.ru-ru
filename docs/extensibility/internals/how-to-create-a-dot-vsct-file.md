---
title: 'Как: Создать . Vsct Файл (англ.) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708106"
---
# <a name="how-to-create-a-vsct-file"></a>Как: Создать файл .vsct

Существует несколько способов создания конфигурации командной таблицы Visual Studio на основе XML *(.vsct)* файла.

- Вы можете создать новый [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage в шаблоне пакета.

- Для создания файла из существующего файла *.ctc* можно использовать компилятор конфигурации командной таблицы На основе XML *Vsct.exe.*

- Вы можете использовать *Vsct.exe* для создания файла *.vsct* из существующего файла *.cto.*

- Вы можете вручную создать новый файл *.vsct.*

  В этой статье объясняется, как вручную создать новый файл *.vsct.*

### <a name="to-manually-create-a-new-vsct-file"></a>Для ручного создания нового файла .vsct

1. Запустите среду [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. В меню **Файл** укажите пункт **Создать**, а затем выберите пункт **Файл**.

3. В панели **шаблонов** нажмите **XML File,** а затем нажмите **Open**.

4. В меню **View** нажмите **«Свойства»,** чтобы отобразить свойства файла XML.

5. В окне **Свойств** нажмите кнопку **«Просмотр»** на **свойстве Schemas.**

6. В списке схем XSD выберите схему *vsct.xsd.* Если его нет в списке, нажмите **Добавить,** а затем найти файл на локальном диске. Нажмите **OK,** когда вы закончите.

7. В файле XML введите *<CommandTable,* а затем нажмите **Tab.** Закройте тег, *>* введя .

    Это действие создает базовый файл *.vsct.*

8. Заполните элементы файла XML, которые вы хотите добавить, в соответствии со ссылкой на [схему VSCT XML.](../../extensibility/vsct-xml-schema-reference.md) Для получения дополнительной информации [см.](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Как: Создать файл .vsct из существующего файла .ctc

Можно создать файл *.vsct* на основе XML из существующего исходного файла *.ctc..* Таким образом можно воспользоваться новым форматом компилятора таблицы команд [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе XML (VSCT).

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC

1. Получите копию языка Perl.

2. Получить копию сценария Perl *ConvertCTCToVSCT.pl*, как правило, расположенных в * \<Visual Studio SDK пути установки>»VisualStudioIntegration »Инструменты»Bin* папки.

3. Получите копию исходного файла *.ctc,* который вы хотите преобразовать.

4. Поместите файлы в один каталог.

5. В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] окне запроса команды перейдите в каталог.

6. Type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    где *PkgCmd.ctc* — это название файла *.ctc,* а *PkgCmd.vsct* — это название файла *.vsct,* который вы хотите создать.

    Это действие создает новый исходный файл таблицы *командный xML .vsct* XML. Вы можете компилировать файл с помощью *Vsct.exe,* компилятора VSCT, как и любой другой файл *.vsct.*

   > [!NOTE]
   > Вы можете улучшить читаемость файла *.vsct,* переформатируя комментарии XML.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Как: Создать файл .vsct из существующего файла .cto

Вы можете создать файл *.vsct* на основе XML из существующего двоичного *файла .cto.* Это позволяет воспользоваться преимуществами нового формата компилятора таблицы команд. Этот процесс работает, даже если файл *.cto* был составлен из файла *.ctc.* Вы можете отсеивать и компилировать файл *.vsct* в другой файл .cto.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Создание файла VSCT на основе файла CTO

1. Получение копий файла *.cto* и соответствующего файла *.ctsym.*

2. Поместите файлы в тот же каталог, что и компилятор *vsct.exe.*

3. В запросе команды Visual Studio перейдите в каталог, содержащий файлы *.cto* и *.ctsym.*

4. Type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     где \<\> ктофиле является названием файла \< *.cto,* vsctfilename\> — это название файла \< *.vsct,* которое вы хотите создать, а симфилиимен —\> это название файла *.ctsym.*

     Этот процесс создает новый файл компилятора таблицы компиляции *командный окни .vsct* XML. Вы можете отсеивать и компилировать файл с *vsct.exe*, компилятор vsct, как и любой другой файл *.vsct.*

## <a name="compile-the-code"></a>Компиляция кода
 Простое добавление файла *.vsct* в проект не приводит к его компиляции. Вы должны включить его в процесс сборки.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Добавление файла .vsct в компиляцию проекта

1. Откройте файл проекта в редакторе. Если проект загружен, необходимо сначала выгрузить его.

2. Добавьте [элемент ItemGroup,](../../msbuild/itemgroup-element-msbuild.md) содержащий `VSCTCompile` элемент, показанный в следующем примере.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Элемент `ResourceName` всегда должен быть `Menus.ctmenu`настроен на .

3. Если проект содержит файл *.resx,* добавьте `EmbeddedResource` `MergeWithCTO` элемент, содержащий элемент, как показано в следующем примере:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Эта разметка должна `ItemGroup` находиться внутри элемента, содержащего встроенные ресурсы.

4. Откройте файл пакета, обычно названный * \<\>ProjectName Package.cs* или * \<ProjectName\>Package.vb*, в редакторе.

5. Добавьте `ProvideMenuResource` атрибут в класс пакетов, как показано в следующем примере.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Значение первого параметра должно `ResourceName` соответствовать значению атрибута, определяемого в файле проекта.

## <a name="see-also"></a>См. также
- [Авторские файлы .vsct](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Таблица команд Visual Studio (.vsct) файлов](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Ссылка на схему VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
