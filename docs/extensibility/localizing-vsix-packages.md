---
title: "Локализация пакетов VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Локализация пакета"
  - "локализация расширения"
  - "Локализация развертывания"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Локализация пакетов VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Для локализации пакета VSIX создать файл Extension.vsixlangpack для каждого требуемого языка и поместить эти файлы в папке. После установки локализованного пакета вместе с локализованное описание отображается локализованное имя расширения. Если указать локализованный файл лицензии или URL\-адрес, указывающий на локализованные сведения, они также отображаются.  
  
 Если содержимое пакета VSIX включает в себя VSPackage, который добавляет команды меню или другой пользовательский Интерфейс в разделе [Локализация команды меню](../extensibility/localizing-menu-commands.md) сведения о локализации новые элементы пользовательского интерфейса.  
  
## Структура каталогов  
 Когда пользователь устанавливает расширение, **расширения и обновления** проверяет верхний уровень пакета VSIX на наличие папки, имя которого соответствует языку Visual Studio на целевом компьютере. Если **расширения и обновления** находит a .vsixlangpack файл в папке, он подставляет локализованные значения из данного файла вместо соответствующих значений в файле VSIXMANIFEST. Эти значения отображаются при установке расширения. Следующий пример показывает структуру каталогов для пакета VSIX, который локализован на испанский \(es\-ES\) и французский \(fr\-FR\).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\] .xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  Шаблоны проекта VSIX поддерживается в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Создать манифест VSIX и назовите его source.extension.vsixmanifest. Если Visual Studio создает проект, она копирует содержимое этого файла в файл Extension.VsixManifest в пакете VSIX.  
  
## Файл Extension.vsixlangpack  
 Файл Extension.vsixlangpack следует [Схема языкового пакета VSIX](../extensibility/vsx-language-pack-schema-reference.md). Эта схема имеет [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) корневого элемента и этих четырех дочерних элементов: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), и [лицензии](../extensibility/license-element-vsix-language-pack-schema.md). Эти дочерние элементы соответствуют `Name`, `Description`, `MoreInfoURL`, и `License` дочерними элементами элемента `Identifier` в файле Extension.vsixmanifest.  
  
 При создании файла vsixlangpack необходимо задать `Include in Vsix` Свойства `true`. В противном случае — локализованного текста установки будет игнорироваться.  
  
#### Задание включения в Vsix\-свойство  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши файл Extension.vsixlangpack и нажмите кнопку **Свойства**.  
  
2.  В таблице свойств нажмите кнопку **Включить в Vsix**, и задайте для него значение `true`.  
  
## Пример  
  
### Описание  
 В следующем примере показано соответствующих частей файл Extension.vsixmanifest, а также соответствующий файл Extension.vsixlangpack для испанского языка. Значения из языкового пакета заменяют значения из манифеста, если установлен испанский язык Visual Studio на целевом компьютере.  
  
### Код  
 \[Extension.vsixmanifest\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 \[Extension.vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## См. также  
 [Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Шаблон проекта VSIX](../extensibility/vsix-project-template.md)