---
title: Локализация команд меню | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce3cbbf101e357f761ffaf256d0b130a0c005fdb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561713"
---
# <a name="localizing-menu-commands"></a>Локализация команд меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [локализация команд меню](https://docs.microsoft.com/visualstudio/extensibility/localizing-menu-commands).  
  
Локализованный текст можно предоставить для меню и панель инструментов, команды путем создания локализованного vsct-файлы и локализованного RESX-файлы для пакета VSPackage, а затем обновить файлы проекта для включения изменений.  
  
 Сведения о локализации процедуру установки, см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Локализация имен команд  
 В пакеты VSPackage команды меню и кнопки панели инструментов определяются в vsct-файле.  
  
1.  В **обозревателе решений**, измените имя файла vsct из *filename*.vsct для *filename*.en-US.vsct.  
  
2.  Создайте копию *filename*.en-US.vsct для каждого языка локализации.  
  
     Имя каждой копии *filename*. *Языковой стандарт*.vsct, где *языкового стандарта* — это имя определенного языка и региональных параметров. Список значений имени языка и региональных параметров, см. в разделе [Locale IDs Assigned by Microsoft](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
     Эти *filename*. *Языковой стандарт*vsct-файлов будет содержать текст локализованного меню для своего пакета.  
  
3.  Откройте каждый *filename*. *Языковой стандарт*vsct-файл для локализации текста.  
  
    1.  Изменить [ButtonText](../extensibility/buttontext-element.md) элементы со значениями в соответствии с определенного языка.  
  
    2.  Будет предоставляться локализованные значки, измените [точечного рисунка](../extensibility/bitmap-element.md) значения, чтобы указать целевые файлы.  
  
     Следующий пример показывает английский и испанский текст кнопки для команды открыть окно инструментов семейного дерева обозревателя.  
  
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
 Текстовые ресурсы, отличные от имен команд определяются в файлах ресурсов (RESX).  
  
1.  Переименуйте VSPackage.resx VSPackage.en-US.resx.  
  
2.  Создайте копию файла VSPackage.en-US.resx для каждого локализованного языка.  
  
     Имя каждой копии VSPackage. *Языкового стандарта*.resx, где *языкового стандарта* — это имя определенного языка и региональных параметров.  
  
3.  Переименуйте Resources.resx именами Resources.en-US.resx.  
  
4.  Создайте копию файла именами Resources.en-US.resx для каждого локализованного языка.  
  
     Имя каждой копии ресурсы. *Языкового стандарта*.resx, где *языкового стандарта* — это имя определенного языка и региональных параметров.  
  
5.  Откройте каждый RESX-файл, чтобы изменить строковые значения, подходящие для конкретного языка и региональных параметров. В следующем примере показано определение локализованный ресурс строки заголовка окна инструментов.  
  
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
  
## <a name="incorporating-localized-resources-into-the-project"></a>Включение локализованных ресурсов в проект  
 Необходимо изменить файл assemblyinfo.cs и файл проекта, чтобы включить локализованные ресурсы.  
  
1.  Из **свойства** узел в **обозревателе решений**, откройте файл assemblyinfo.cs или assemblyinfo.vb в редакторе.  
  
2.  Добавьте следующую запись.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Таким образом задается английского (США) по умолчанию.  
  
3.  Выгрузите проект.  
  
4.  Откройте файл проекта в редакторе.  
  
5.  Найдите `ItemGroup` элемент, содержащий `EmbeddedResource` элементов.  
  
6.  В `EmbeddedResource` замените элемент, который вызывает VSPackage.en-US.resx `ManifestResourceName` элемент с `LogicalName` элемент, значение `VSPackage.en-US.Resources`, как показано ниже.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Для каждого локализованного языка, скопируйте `EmbeddedResource` элемент для VsPackage.en США, а также набор **Include** атрибут и **LogicalName** Копировать в целевой языковой стандарт, как показано в следующем примере элемент Пример.  
  
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
  
     Это создает основную сборку и сборки ресурсов для каждого языка. Сведения о локализации процесс развертывания, см. в разделе [локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Команды MenuCommand и OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Глобализация и локализация](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

