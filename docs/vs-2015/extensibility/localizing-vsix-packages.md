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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439755"
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете локализовать пакета VSIX, создав файл Extension.vsixlangpack для каждого целевого языка и поместить эти файлы в папке. При установке локализованного пакета локализованное описание отобразите локализованное имя расширения. Если вы указали локализованный файл лицензии или URL-адрес, указывающий на локализованные сведения, они также отображаются.  
  
 Если содержимое пакета VSIX включает пакет VSPackage, который добавляет команды меню или другой пользовательский Интерфейс, см. в разделе [локализация команд меню](../extensibility/localizing-menu-commands.md) сведения о локализации новых элементов пользовательского интерфейса.  
  
## <a name="directory-structure"></a>Структура каталогов  
 Когда пользователь устанавливает расширение, **расширения и обновления** проверяет верхний уровень пакета VSIX для папки, имя которого соответствует языку Visual Studio конечного компьютера. Если **расширения и обновления** находит .vsixlangpack файл в папке, он подставляет локализованные значения в этом файле, соответствующих значений в файле VSIXMANIFEST. Эти значения отображаются при установке расширения. В следующем примере структуру каталогов для пакета VSIX, который локализован на испанский (es-ES) и французского (fr-FR).  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 [Content_Types].xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
> Шаблоны проектов VSIX поддерживается в [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] создать манифест VSIX и назовите его source.extension.vsixmanifest. Когда Visual Studio создает проект, он копирует содержимое этого файла в Extension.VsixManifest в пакете VSIX.  
  
## <a name="the-extensionvsixlangpack-file"></a>Файл Extension.vsixlangpack  
 Файл Extension.vsixlangpack следует [схема языкового пакета VSIX](../extensibility/vsx-language-pack-schema-reference.md). Эта схема имеет [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) корневого элемента и эти четыре дочерних элемента: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), и [лицензии](../extensibility/license-element-vsix-language-pack-schema.md). Эти дочерние элементы соответствуют `Name`, `Description`, `MoreInfoURL`, и `License` дочерними элементами элемента `Identifier` элемент файл Extension.vsixmanifest.  
  
 При создании файла vsixlangpack, необходимо задать `Include in Vsix` свойства `true`. В противном случае текст локализованного установочного будет игнорироваться.  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Чтобы задать включают свойства Vsix  
  
1. В **обозревателе решений**, щелкните правой кнопкой мыши файл Extension.vsixlangpack и нажмите кнопку **свойства**.  
  
2. В сетке свойств нажмите кнопку **включить в Vsix**и присвойте ему значение `true`.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано нужные части файл Extension.vsixmanifest, а также соответствующий файл Extension.vsixlangpack для испанского языка. Значения из языкового пакета замените значения из манифеста, если задано значение испанский языковой стандарт Visual Studio для конечного компьютера.  
  
### <a name="code"></a>Код  
 [Extension.vsixmanifest]  
  
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
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>См. также  
 [Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Шаблон проекта VSIX](../extensibility/vsix-project-template.md)
