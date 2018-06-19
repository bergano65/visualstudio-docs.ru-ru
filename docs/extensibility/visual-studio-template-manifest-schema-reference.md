---
title: Справочник по схемам манифеста шаблона Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26f346329e4c0fa2defe6bc4ff6373226be72beb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142585"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Справочник по схемам манифеста шаблона Visual Studio
Эта схема описывает формат файла манифеста (.vstman) Visual Studio шаблона, созданного для шаблонов проектов и элементов для Visual Studio и расположение и другие сведения о шаблоне.  
  
 : Существует отдельный элемент и каталоги шаблона проекта, манифест никогда не следует включать в себя элементов и шаблоны проектов.  
  
> [!IMPORTANT]
>  Этот манифест доступна, начиная с Visual Studio 2017 г.  
  
## <a name="vstemplatemanifest-element"></a>Элемент VSTemplateManifest  
 Корневой элемент манифеста.  
  
### <a name="attributes"></a>Атрибуты  
  
-   **Версия**: строка, представляющая версию шаблона манифеста. Обязательно.  
  
-   **Языковой стандарт**: строка, представляющая язык или язык и региональные стандарты шаблон манифеста. Значение языка применяется ко всем шаблонам, поэтому необходимо использовать отдельный манифест для каждого языкового стандарта. Необязательный.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **VSTemplateContainer** необязательно.  
  
-   **VSTemplateDir** необязательно.  
  
### <a name="parent-element"></a>Элемент Parent  
 Отсутствует.  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Контейнер шаблона манифеста элементов. Манифест содержит один контейнер шаблона для каждого шаблона, которые он определяет.  
  
### <a name="attributes"></a>Атрибуты  
 **VSTemplateType** : строковое значение, указывающее тип шаблона (`"Project"`, `"Item"`, или `"ProjectGroup"`). Обязательно  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePathOnDisk**: относительный путь к файлу шаблона на диске. Это расположение также определяет размещение шаблона в шаблон дерева, показанного в **новый проект** или **новый элемент** диалогового окна. Для развернутых каталога и отдельные файлы шаблонов этот путь ссылается на каталог, содержащий файлы шаблонов. Для шаблонов, развернутый как ZIP-файл этот путь должен быть путь к ZIP-файл.  
  
-   **VSTemplateHeader** : A [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент, описывающий заголовок.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Указывает каталог, где расположен шаблон. Манифест может содержать несколько **VSTemplateDir** записи для предоставления локализованного имени и сортировки упорядочение для каталогов для управления их появления в дерево категории шаблонов.  
  
 Из-за своей конструкции **VSTemplateDir** отображаются записи только в указанных манифестов отличных от языкового стандарта.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
-   **RelativePath**: путь к шаблону. Может существовать только одна запись на путь, поэтому для всех манифестов выигрывает первый.  
  
-   **LocalizedName**: A **NameDescriptionIcon** элемент, который задает локализованное имя. Необязательный.  
  
-   **SortOrder** : строка, определяющая порядок сортировки. Необязательный.  
  
-   **ParentFolderOverrideName**: переопределенное имя родительской папки. Необязательный. Этот элемент имеет **имя** атрибута, который является строковое значение, указывающее имя.  
  
### <a name="parent-element"></a>Элемент Parent  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Указывает имя и описание, возможно для локализованных шаблонов. В разделе **LocalizedName** выше.  
  
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