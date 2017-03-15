---
title: "Справочник по схеме манифеста шаблона Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Справочник по схемам манифеста шаблона Visual Studio
Эта схема описывает формат файлов манифеста (.vstman) шаблона Visual Studio, созданных для шаблона проекта или элемента в Visual Studio и расположение и другие важные сведения о шаблоне.  
  
 : Существует отдельный элемент и каталоги шаблона проекта, манифест никогда не должны сочетание элементов и шаблоны проектов.  
  
> [!IMPORTANT]
>  Этот манифест доступен, начиная с Visual Studio 2017 г.  
  
## <a name="vstemplatemanifest-element"></a>Элемент VSTemplateManifest  
 Корневой элемент манифеста.  
  
### <a name="attributes"></a>Атрибуты  
  
-   **Версия**: строка, представляющая версию шаблона манифеста. Обязательный.  
  
-   **Языковой стандарт**: строка, представляющая язык или языки шаблон манифеста. Значение языка применяется ко всем шаблонам, поэтому необходимо использовать отдельный манифест для каждого языкового стандарта. Необязательный.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **VSTemplateContainer** необязательно.  
  
-   **VSTemplateDir** необязательно.  
  
### <a name="parent-element"></a>Элемент Parent  
 Отсутствует.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Контейнер шаблона манифеста элементов. Манифест содержит один контейнер шаблона для каждого шаблона, которые он определяет.  
  
### <a name="attributes"></a>Атрибуты  
 **VSTemplateType** : строковое значение, указывающее тип шаблона (`"Project"`, `"Item"`, или `"ProjectGroup"`). Обязательное  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePathOnDisk**: относительный путь к файлу шаблона на диске. Это расположение также определяет положение шаблона в дереве шаблона, показанный на **новый проект** или **новый элемент** диалогового окна. Для шаблоны, развертываемые как каталог и отдельных файлов этот путь ссылается на каталог, содержащий файлы шаблонов. Для шаблоны, развертываемые как ZIP-файл этот путь должен быть путь к ZIP-файл.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент, описывающий заголовок.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Указывает каталог, где расположен шаблон. Манифест может содержать несколько **VSTemplateDir** записи для предоставления локализованного имени и сортировки, упорядочение для каталогов, управлять их внешним видом в дерево категорий шаблонов.  
  
 Из-за своей конструкции **VSTemplateDir** отображаются записи только в указанных манифестов отличных от языкового стандарта.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePath**: путь к шаблону. Могут быть только одна запись для каждого пути, поэтому для все манифесты выигрывает первый из них.  
  
-   **LocalizedName**: A **NameDescriptionIcon** элемент, который определяет локализованное имя. Необязательный.  
  
-   **SortOrder** : строка, указывающая порядок сортировки. Необязательный.  
  
-   **ParentFolderOverrideName**: переопределенный имя родительской папки. Необязательный. Этот элемент имеет **имя** атрибута, который является строковое значение, указывающее имя.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Указывает имя и описание, например для локализованных шаблонов. В разделе **LocalizedName** выше.  
  
### <a name="attributes"></a>Атрибуты  
  
-   **Пакет**: строковое значение, указывающее пакета. Необязательный.  
  
-   **Идентификатор**: строковое значение, указывающее идентификатор. Необязательный.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-element"></a>Элемент Parent  
 **LocalizedName**  
  
## <a name="examples"></a>Примеры  
 Ниже приведен пример файла .vstman шаблона проекта.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Ниже приведен пример файла .vstman шаблона элемента.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```
