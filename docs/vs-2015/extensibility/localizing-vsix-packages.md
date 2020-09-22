---
title: Локализация пакетов VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6143b21884bc92ac79ae0fd7292a11780fec4478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842585"
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете локализовать пакет VSIX, создав файл Extension. всикслангпакк для каждого целевого языка и поместив их в соответствующую папку. При установке локализованного пакета локализованное имя расширения отображается вместе с локализованным описанием. Если указать локализованный файл лицензии или URL-адрес, указывающий на локализованные сведения, они также будут отображаться.  
  
 Если содержимое пакета VSIX содержит пакет VSPackage, который добавляет команды меню или другой пользовательский интерфейс, см. раздел [команды меню локализации](../extensibility/localizing-menu-commands.md) для получения сведений о локализации новых элементов пользовательского интерфейса.  
  
## <a name="directory-structure"></a>Структура каталогов  
 Когда пользователь устанавливает расширение, **расширения и обновления** проверяют верхний уровень пакета VSIX для папки, имя которой соответствует языковому стандарту Visual Studio конечного компьютера. Если **расширения и обновления** обнаруживают всикслангпакк-файл в папке, он заменяет локализованные значения в этом файле соответствующими значениями в VSIXMANIFEST-файле. Эти значения отображаются при установке расширения. В следующем примере показана структура каталогов для пакета VSIX, который локализован на Испанский (ES-ES) и французский (fr-FR).  
  
 MyExtension.dll  
  
 Расширение. vsixmanifest  
  
 [Content_Types]. XML  
  
 es-ES  
  
 Расширение. всикслангпакк  
  
 fr-FR  
  
 Расширение. всикслангпакк  
  
> [!NOTE]
> Поддерживаемые VSIX шаблоны проектов в [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Создайте манифест VSIX и назовите его Source. extension. vsixmanifest. Когда Visual Studio выполняет сборку проекта, он копирует содержимое этого файла в Extension. VsixManifest в пакете VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Файл Extension. всикслангпакк  
 Файл Extension. всикслангпакк соответствует [схеме языкового пакета VSIX](../extensibility/vsx-language-pack-schema-reference.md). Эта схема имеет корневой элемент [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) , и эти четыре дочерних элемента: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [локализеддескриптион](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [мореинфаурл](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)и [License](../extensibility/license-element-vsix-language-pack-schema.md). Эти дочерние элементы соответствуют `Name` `Description` `MoreInfoURL` `License` дочерним элементам,, и `Identifier` элемента файла Extension. vsixmanifest.  
  
 При создании файла всикслангпакк необходимо задать `Include in Vsix` для свойства значение `true` . В противном случае локализованный текст установки будет проигнорирован.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Задание свойства include в VSIX  
  
1. В **Обозреватель решений**щелкните правой кнопкой мыши файл Extension. всикслангпакк и выберите пункт **свойства**.  
  
2. В сетке свойств щелкните **включить в VSIX**и присвойте ему значение `true` .  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Description  
 В следующем примере показаны соответствующие части файла Extension. vsixmanifest вместе с соответствующим файлом Extension. всикслангпакк для испанского. Значения из языкового пакета заменяют значения из манифеста, если для языка Visual Studio целевого компьютера задано значение испанский.  
  
### <a name="code"></a>Код  
 [Extension. vsixmanifest]  
  
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
  
 [Extension. всикслангпакк]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>См. также:  
 [Элемент LanguagePack в VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Шаблон проекта VSIX](../extensibility/vsix-project-template.md)
