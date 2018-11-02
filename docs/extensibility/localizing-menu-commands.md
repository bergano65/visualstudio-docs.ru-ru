---
title: Локализация команд меню | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8eb9e566f4f5916961a95a1c61f8fdcbb689f1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876221"
---
# <a name="localize-menu-commands"></a>Локализация команд меню
Можно предоставить локализованный текст для команды меню и панели инструментов, создание локализованных *.vsct* файлы и локализованных *.resx* файлы для пакета VSPackage, а затем обновить файлы проекта для включения изменения.  
  
 Сведения о локализации процедуру установки, см. в разделе [пакетов VSIX локализации](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localize-command-names"></a>Локализация имен команд  
 Пакеты VSPackage, команды меню и кнопки панели инструментов, определяются в *.vsct* файла.  
  
1. В **обозревателе решений**, измените имя *.vsct* файла из *filename.vsct* для *filename.en US.vsct*.  
  
2. Создайте копию *filename.en US.vsct* для каждого языка локализации.  
  
    Имя каждой копии *filename. {} Языковой стандарт} .vsct*, где *{языковой стандарт}* — это имя определенного языка и региональных параметров. Список значений имени языка и региональных параметров, см. в разделе [идентификаторы, назначаемые Microsoft](/windows/uwp/publish/supported-languages).  
  
    Эти *имя файла. Locale.vsct* файлы будут содержать текст локализованного меню для своего пакета.  
  
3. Откройте каждый *имя файла. Locale.vsct* файл для локализации текста.  
  
   1. Изменить [ButtonText](../extensibility/buttontext-element.md) элементы со значениями в соответствии с определенного языка.  
  
   2. Будет предоставляться локализованные значки, измените [точечного рисунка](../extensibility/bitmap-element.md) значения, чтобы указать целевые файлы.  
  
      Следующий пример показывает английский и испанский текст кнопки для команды открыть окно инструментов семейного дерева обозревателя.  
  
      [*FamilyTree.en US.vsct*]  
  
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
  
    [*FamilyTree.es ES.vsct*]  
  
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
  
## <a name="localize-other-text-resources"></a>Локализация ресурсов других текста  
 Текстовые ресурсы, отличные от имен команд определяются в ресурсе (*.resx*) файлы.  
  
1.  Переименуйте *VSPackage.resx* для *VSPackage.en-US.resx*.  
  
2.  Создайте копию *VSPackage.en-US.resx* файл для каждого языка локализации.  
  
     Имя каждой копии *VSPackage. {} Языковой стандарт} .resx*, где *{языковой стандарт}* — это имя определенного языка и региональных параметров.  
  
3.  Переименуйте *Resources.resx* для *именами Resources.en-US.resx*.  
  
4.  Создайте копию *именами Resources.en-US.resx* файл для каждого языка локализации.  
  
     Имя каждой копии *ресурсы. {} Языковой стандарт} .resx*, где *{языковой стандарт}* — это имя определенного языка и региональных параметров.  
  
5.  Откройте каждый *.resx* файл для изменения строки значения соответствующим образом для определенного языка и региональных параметров. В следующем примере показано определение локализованный ресурс строки заголовка окна инструментов.  
  
     [*Именами Resources.en-US.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [*Resources.es-ES.resx*]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporate-localized-resources-into-the-project"></a>Включить локализованные ресурсы в проект  
 Необходимо изменить *assemblyinfo.cs* файл и файл проекта для включения в локализованные ресурсы.  
  
1.  Из **свойства** узел в **обозревателе решений**откройте *assemblyinfo.cs* или *assemblyinfo.vb* в редакторе.  
  
2.  Добавьте следующую запись.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Таким образом задается английского (США) по умолчанию.  
  
3.  Выгрузите проект.  
  
4.  Откройте файл проекта в редакторе.  
  
5.  Найдите `ItemGroup` элемент, содержащий `EmbeddedResource` элементов.  
  
6.  В `EmbeddedResource` элемент, который вызывает *VSPackage.en-US.resx*, замените `ManifestResourceName` элемент с `LogicalName` элемент, значение `VSPackage.en-US.Resources`, как показано ниже.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Для каждого локализованного языка, скопируйте `EmbeddedResource` элемент для `VsPackage.en-US`и задайте **Include** атрибут и **LogicalName** Копировать в целевой языковой стандарт, как показано в следующем примере элемент Пример.  
  
8.  К каждому локализованные `VSCTCompile` элемента, добавьте `ResourceName` элемента, который указывает `Menus.ctmenu`, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Сохраните файл проекта и перезагрузить проект.  
  
10. Выполните построение проекта.  
  
     Это создает основную сборку и сборки ресурсов для каждого языка. Сведения о локализации процесс развертывания, см. в разделе [пакетов VSIX, локализация](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Команды MenuCommand и OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)