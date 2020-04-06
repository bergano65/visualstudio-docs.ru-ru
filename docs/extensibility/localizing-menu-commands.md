---
title: Локализация Команд меню Документы Майкрософт
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702948"
---
# <a name="localize-menu-commands"></a>Локализация команд меню

Можно предоставить локализованный текст для команд меню и панели инструментов, создав локализованные файлы *.vsct* и локализованные *файлы .resx* для вашего VSPackage, а затем обновив файлы проекта для включения изменений.

Для получения информации о том, как локализовать опыт установки, [см.](../extensibility/localizing-vsix-packages.md)

## <a name="localize-command-names"></a>Локализовать имена команд

В VSPackages команды меню и кнопки панели инструментов определяются в файле *.vsct.*

1. В **Solution Explorer**измените название файла *.vsct* с *filename.vsct* на *filename.en-US.vsct.*

2. Сделайте копию *filename.en-US.vsct* для каждого локализованного языка.

    Назовите *каждое имя файла копии. Локаль.vsct*, где *«Locale»* является особым названием культуры. Список значений названий [Locale IDs assigned by Microsoft](/windows/uwp/publish/supported-languages)культуры см.

    Эти *имена файлов. Файлы Locale.vsct* будут содержать локальный текст меню для вашего пакета.

3. Откройте каждое *имя файла. Файл Locale.vsct* для локализации текста.

   1. Изменять значения элемента [ButtonText](../extensibility/buttontext-element.md) в соответствии с определенным языком.

   2. Если вы предоставите локализованные значки, измените значения [Bitmap,](../extensibility/bitmap-element.md) чтобы указать на целевые файлы.

      Ниже приводится текст английской и испанской кнопок для команды, чтобы открыть окно инструмента Family Tree Explorer.

      *FamilyTree.en-US.vsct*

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    -*FamilyTree.es-ES.vsct*

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Локализация других текстовых ресурсов

Текстовые ресурсы, кроме имен команд, определяются в файлах ресурсов *(.resx).*

1. Переименуй *VSPackage.resx* на *VSPackage.en-US.resx*.

2. Сделайте копию файла *VSPackage.en-US.resx* для каждого локализованного языка.

     Назовите каждую копию *VSPackage. Locale.resx*, где *«Locale»* — это особое название культуры.

3. Переименуй *Ресурсы.resx* на *Resources.en-US.resx*.

4. Сделайте копию файла *Resources.en-US.resx* для каждого локализованного языка.

     Назовите каждую копию *Ресурсы. Locale.resx*, где *«Locale»* — это особое название культуры.

5. Откройте каждый файл *.resx,* чтобы изменить значения строки в соответствии с определенным языком и культурой. В следующем примере показано определение локализованного ресурса для панели заголовка окна инструмента.

     -*Resources.en-US.resx*

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     -*Resources.es-ES.resx*

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Включение локализованных ресурсов в проект

Необходимо изменить *assemblyinfo.cs* файл и файл проекта, чтобы включить локализованные ресурсы.

1. От узла **Свойств** в **Solution Explorer**, открыть *assemblyinfo.cs* или *assemblyinfo.vb* в редакторе.

2. Добавьте следующую запись.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Это устанавливает американский английский язык в качестве языка по умолчанию.

3. Разгрузите проект.

4. Откройте файл проекта в редакторе.

5. В корневой `Project` `PropertyGroup` элемент добавьте `UICulture` элемент с элементом, который соответствует языку по умолчанию.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Это устанавливает американский английский язык как культуру uI по умолчанию для элементов управления Windows Presentation Foundation (WPF).

6. Найдите `ItemGroup` элемент, `EmbeddedResource` содержащий элементы.

7. В `EmbeddedResource` элементе, который вызывает *VSPackage.en-US.resx,* замените `ManifestResourceName` элемент элементом, `LogicalName` который установлен на, `VSPackage.en-US.Resources`следующим образом:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Для каждого локализованного языка `EmbeddedResource` копируйте элемент для `VsPackage.en-US`и установите элемент **«Включить»** и элемент **LogicalName** копии в целевой язык.

9. К каждому `VSCTCompile` локализованному `ResourceName` элементу добавьте элемент, который указывает на, `Menus.ctmenu`как показано в следующем примере:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Сохранить файл проекта и перезагрузить проект.

11. Создайте проект.

     Это создает основную сборку и сборку ресурсов для каждого языка. Для получения информации о локализации процесса развертывания [см.](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>См. также

- [Расширить меню и команды](../extensibility/extending-menus-and-commands.md)
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
