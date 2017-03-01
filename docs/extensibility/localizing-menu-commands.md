---
title: "Локализация команды меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 869a1c878a591e6b755fc1311132e159d38ffe8f
ms.lasthandoff: 02/22/2017

---
# <a name="localizing-menu-commands"></a>Локализация команды меню
Можно предоставить локализованный текст меню и панели инструментов команды путем создания локализованных vsct-файлы и локализованного RESX-файлы для VSPackage, а затем обновить файлы проекта для включения изменений.  
  
 Сведения о локализации процедуру установки см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Локализация имен команд  
 В пакеты VSPackage команды меню и кнопки панели инструментов определяются в файле .vsct.  
  
1.  В **обозревателе решений**, измените имя файла .vsct из *filename*.vsct для *filename*.en US.vsct.  
  
2.  Создайте копию *filename*.en-US.vsct для каждого языка локализации.  
  
     Имя каждой копии *filename*.* Языковой стандарт*.vsct, где *языкового стандарта* является именем определенного языка и региональных параметров. Список имен и значений языка и региональных параметров см. в разделе [языкового стандарта, назначаемые Microsoft](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Эти *filename*.* Языковой стандарт*vsct-файлах будет содержать текст локализованного меню для пакета.  
  
3.  Откройте каждый *filename*.* Языковой стандарт*файла .vsct для локализации текста.  
  
    1.  Изменить [ButtonText](../extensibility/buttontext-element.md) элемент значения соответствующим образом для конкретного языка.  
  
    2.  При указании локализованных значки, измените [точечный рисунок](../extensibility/bitmap-element.md) значений для указания целевых файлов.  
  
     В следующем примере показано английский и испанский текст кнопки для команды открыть окно инструментов семейного дерева обозревателя.  
  
     [FamilyTree.en-US.vsct]  
  
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
  
     [FamilyTree.es-ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Локализация ресурсов других текста  
 Текстовые ресурсы, отличные от имен команд определены в файлах ресурсов (RESX).  
  
1.  Переименуйте VSPackage.resx VSPackage.en-US.resx.  
  
2.  Создайте копию файла VSPackage.en-US.resx для каждого языка.  
  
     Имя каждой копии VSPackage. *Языкового стандарта*.resx, где *языкового стандарта* является именем определенного языка и региональных параметров.  
  
3.  Переименуйте Resources.resx именами Resources.en-US.resx.  
  
4.  Создайте копию файла именами Resources.en-US.resx для каждого языка.  
  
     Имя каждой копии ресурсы. *Языкового стандарта*.resx, где *языкового стандарта* является именем определенного языка и региональных параметров.  
  
5.  Откройте каждый файл .resx, для изменения значения строки, необходимые для конкретного языка и региональных параметров. Пример определения локализованные строки заголовка окна инструментов.  
  
     [Именами Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Включение локализованные ресурсы в проект  
 Необходимо изменить файл assemblyinfo.cs и файл проекта, чтобы включить локализованные ресурсы.  
  
1.  От **свойства** узел в **обозревателе**, откройте файл assemblyinfo.cs или assemblyinfo.vb в редакторе.  
  
2.  Добавьте следующую запись.  
  
    ```c#  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Это задает английский (США) в качестве языка по умолчанию.  
  
3.  Выгрузите проект.  
  
4.  Откройте файл проекта в редакторе.  
  
5.  Найдите `ItemGroup` элемент, содержащий `EmbeddedResource` элементы.  
  
6.  В `EmbeddedResource` заменить элемент, который вызывает VSPackage.en-US.resx `ManifestResourceName` элемент с `LogicalName` элемент, значение `VSPackage.en-US.Resources`, как показано ниже.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Для каждого языка локализации, скопируйте `EmbeddedResource` элемент для VsPackage.en США, а также набор **включить** атрибут и **LogicalName** элемент Копировать в целевой языковой стандарт, как показано в следующем примере.  
  
8.  К каждому локализованные `VSCTCompile` элемента, добавьте `ResourceName` элементу, который указывает `Menus.ctmenu`, как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Сохраните файл проекта и перезагрузить проект.  
  
10. Выполните построение проекта.  
  
     Это создает основную сборку и сборок ресурсов для каждого языка. Сведения о локализации процесс развертывания в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Команды MenuCommand и OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Глобализация и локализация](http://msdn.microsoft.com/Library/9a59696b-d89b-45bd-946d-c75da4732d02)
