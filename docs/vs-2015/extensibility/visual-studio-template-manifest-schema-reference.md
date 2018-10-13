---
title: Справочник по схемам манифеста шаблонов Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28301729091333191bcb0c381e37e20d3d9c53aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217102"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Справочник по схемам манифеста шаблонов Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта схема описывает формат файлов манифеста (.vstman) шаблона Visual Studio, созданного для шаблонов проекта или элемента Visual Studio и расположение и другие важные сведения о шаблоне.  
  
 : Существует отдельный элемент и каталоги шаблона проекта, манифест никогда не должен иметь набор шаблонов проектов и элементов.  
  
> [!IMPORTANT]
>  Этот манифест доступен, начиная с версии Visual Studio «15» Preview 2.  
  
## <a name="vstemplatemanifest-element"></a>Элемент VSTemplateManifest  
 Корневой элемент манифеста.  
  
### <a name="attributes"></a>Атрибуты  
  
-   **Версия**: строка, представляющая версию шаблона манифеста. Обязательно.  
  
-   **Языковой стандарт**: строка, представляющая языкового стандарта или национальных настроек шаблона манифеста. Значение языкового стандарта применяется ко всем шаблонам, поэтому необходимо использовать отдельный манифест для каждого языкового стандарта. Необязательный.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **VSTemplateContainer** необязательно.  
  
-   **VSTemplateDir** необязательно.  
  
### <a name="parent-element"></a>Элемент Parent  
 Отсутствует.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Контейнер шаблона манифеста элементов. Манифест содержит один контейнер шаблона для каждого шаблона, который она определяет.  
  
### <a name="attributes"></a>Атрибуты  
 **VSTemplateType** : строковое значение, указывающее тип шаблона (`"Project"`, `"Item"`, или `"ProjectGroup"`). Обязательно  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePathOnDisk**: относительный путь к файлу шаблона на диске. Это расположение также определяет положение шаблона в дереве шаблон, показанный на **новый проект** или **новый элемент** диалоговое окно. Для шаблоны, развертываемые как каталог и отдельных файлов этот путь ссылается на каталог, содержащий файлы шаблонов. Для шаблоны, развертываемые как ZIP-файл этот путь должен содержать путь к ZIP-файл.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент, описывающий заголовок.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Указывает каталог, где находится шаблон. Манифест может содержать несколько **VSTemplateDir** записи для предоставления локализованного имени и сортировки, упорядочение для каталогов, управлять их внешним видом в дерево категорий шаблона.  
  
 Из-за структуры **VSTemplateDir** отображаются записи только в заданные манифесты не языкового стандарта.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePath**: путь к шаблону. Может существовать только одну запись для каждого пути, поэтому первый из них будет предлагаться по умолчанию для всех манифестах.  
  
-   **LocalizedName**: A **NameDescriptionIcon** элемент, который задает локализованное имя. Необязательный.  
  
-   **SortOrder** : строка, указывающая порядок сортировки. Необязательный.  
  
-   **ParentFolderOverrideName**: переопределенное имя родительской папки. Необязательный. Этот элемент имеет **имя** атрибута, который является строковое значение, указывающее имя.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Указывает имя и описание, например для локализованных шаблонов. См. в разделе **LocalizedName** выше.  
  
### <a name="attributes"></a>Атрибуты  
  
-   **Пакет**: строковое значение, указывающее пакета. Необязательный.  
  
-   **Идентификатор**: строковое значение, указывающее идентификатор. Необязательный.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-element"></a>Элемент Parent  
 **LocalizedName**  
  
## <a name="examples"></a>Примеры  
 Ниже приведен пример vstman-файле шаблона проекта.  
  
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
  
 Ниже приведен пример элемента шаблона vstman-файле.  
  
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

