---
title: Команды меню "локализация" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686125"
---
# <a name="localizing-menu-commands"></a>Локализация команд меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете предоставить локализованный текст для команд меню и панели инструментов, создав локализованные файлы. vsct и локализованные файлы. resx для пакета VSPackage, а затем обновив файлы проекта, чтобы внести изменения.  
  
 Сведения о локализации процесса установки см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Локализация имен команд  
 В пакетах VSPackage команды меню и кнопки панели инструментов определены в файле. vsct.  
  
1. В **Обозреватель решений**измените имя файла vsct с *filename*. vsct на *filename*. en-US. vsct.  
  
2. Создайте копию *файла filename*. en-US. vsct для каждого локализованного языка.  
  
    Назовите каждое имя *файла*копии. *Locale*. vsct, где *locale* — это конкретное имя языка и региональных параметров. Список значений имени языка и региональных параметров см. в разделе [идентификаторы языков, назначенные корпорацией Майкрософт](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Эти *имена файлов*. Файлы *locale*. vsct будут содержать локализованный текст меню для пакета.  
  
3. Откройте каждое *имя файла*. Файл *locale*. vsct для локализации текста.  
  
   1. Измените значения элементов [ButtonText](../extensibility/buttontext-element.md) в соответствии с конкретным языком.  
  
   2. Если вы будете предоставлять локализованные значки, измените значения [растровых изображений](../extensibility/bitmap-element.md) , чтобы они указывали на целевые файлы.  
  
      В следующем примере текст кнопки на английском и испанском языках отображается для команды, чтобы открыть окно инструментов обозревателя семейного дерева.  
  
      [FamilyTree. en-US. vsct]  
  
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
  
    [FamilyTree.es-ES. vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Локализация других текстовых ресурсов  
 Текстовые ресурсы, отличные от имен команд, определяются в файлах ресурсов (RESX).  
  
1. Переименуйте VSPackage. resx в VSPackage. en-US. resx.  
  
2. Создайте копию файла VSPackage. en-US. resx для каждого локализованного языка.  
  
     Назовите каждую копию VSPackage. *Locale*. resx, где *locale* — это конкретное имя языка и региональных параметров.  
  
3. Переименуйте Resources. resx в Resources. en-US. resx.  
  
4. Создайте копию файла Resources. en-US. resx для каждого локализованного языка.  
  
     Назовите каждую копию ресурсов. *Locale*. resx, где *locale* — это конкретное имя языка и региональных параметров.  
  
5. Откройте каждый файл. resx, чтобы изменить строковые значения в соответствии с определенным языком и культурой. В следующем примере показано локализованное определение ресурса для заголовка окна инструментов.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Включение локализованных ресурсов в проект  
 Необходимо изменить файл assemblyinfo.cs и файл проекта, чтобы включить локализованные ресурсы.  
  
1. Из узла **Свойства** в **Обозреватель решений**откройте AssemblyInfo.cs или AssemblyInfo. vb в редакторе.  
  
2. Добавьте следующую запись.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     При этом в качестве языка по умолчанию устанавливается английский язык (США).  
  
3. Выгрузить проект.  
  
4. Откройте файл проекта в редакторе.  
  
5. Нахождение `ItemGroup` элемента, содержащего `EmbeddedResource` элементы.  
  
6. В `EmbeddedResource` элементе, который вызывает пакет VSPackage. en-US. resx, замените `ManifestResourceName` элемент `LogicalName` элементом, установленным на `VSPackage.en-US.Resources` , следующим образом.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Для каждого локализованного языка скопируйте  `EmbeddedResource` элемент для VSPackage. en-US и задайте атрибут **include** и элемент **LogicalName** копии в целевом языковом стандарте, как показано в следующем примере.  
  
8. Для каждого локализованного `VSCTCompile` элемента добавьте `ResourceName` элемент, указывающий на `Menus.ctmenu` , как показано в следующем примере.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Сохраните файл проекта и перезагрузите проект.  
  
10. Выполните построение проекта.  
  
     При этом создается Главная сборка и сборки ресурсов для каждого языка. Сведения о локализации процесса развертывания см. в разделе [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md) .  
  
## <a name="see-also"></a>См. также:  
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)   
 [Команды MenuCommand и Олеменукоммандс](../misc/menucommands-vs-olemenucommands.md)   
 [Глобализация и локализация](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
