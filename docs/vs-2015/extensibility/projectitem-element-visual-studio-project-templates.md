---
title: Элемент ProjectItem (шаблоны проектов Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84fb371460bc697660e176ca9df4c984d2b234bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842660"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Элемент ProjectItem (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает файл, включенный в шаблон проекта.  
  
> [!NOTE]
> `ProjectItem`Элемент принимает различные атрибуты в зависимости от того, предназначен ли шаблон для проекта или элемента. В этом разделе описывается `ProjectItem` элемент для шаблонов проектов. Описание `ProjectItem` элемента для шаблонов элементов см. в разделе [элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<ProjectItem>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Задает имя и путь к элементу проекта при создании проекта из шаблона. Этот атрибут полезен для создания структуры каталогов, отличной от структуры каталогов в ZIP-файле шаблона, или для использования замены параметров для создания имени элемента.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию: `false`.|  
|`OpenInEditor`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, должен ли элемент открываться в соответствующем редакторе в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при создании проекта из шаблона.<br /><br /> `OpenInWebBrowser`Атрибуты и `OpenInHelpBrowser` не учитываются для элемента со `OpenInEditor` значением `true` .<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInWebBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, должен ли элемент открываться в веб-браузере при создании проекта из шаблона.<br /><br /> В веб-браузере можно открыть только файлы HTML и текстовые файлы, являющиеся локальными для проекта. Не удается открыть внешние URL-адреса с этим атрибутом.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInHelpBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, должен ли элемент открываться в средстве просмотра справки при создании проекта из шаблона.<br /><br /> В браузере справки можно открыть только файлы HTML и текстовые файлы, являющиеся локальными для проекта. Не удается открыть внешние URL-адреса с этим атрибутом.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenOrder`|Необязательный атрибут.<br /><br /> Задает числовое значение, представляющее порядок, в котором элементы будут открываться в соответствующих редакторах. Все значения должны быть кратными 10. `OpenOrder`Сначала открываются элементы с более высокими значениями.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Указывает файлы или каталоги, добавляемые в проект.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Значение типа `string` , представляющее имя или путь к файлу в ZIP-файле шаблона.  
  
## <a name="remarks"></a>Remarks  
 `ProjectItem` является необязательным дочерним элементом `Project` .  
  
 `TargetFileName`Атрибут можно использовать для создания структуры каталогов, отличной от структуры каталогов в ZIP-файле шаблона. Например, если файл `MyFile.vb` существует в корне ZIP-файла шаблона, но вы хотите поместить файл в каталог `CustomFiles` , указанный во всех проектах, созданных на основе шаблона, используйте следующий код XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`Атрибут также можно использовать для переименования файлов, содержащих международные символы в именах файлов. Например, ZIP-файл шаблона не может содержать имена файлов с символами Юникода, поэтому файл необходимо переименовать, прежде чем его можно будет сжать в ZIP-файл. `TargetFileName`Атрибут можно использовать для возвращения имени файла к исходному имени файла в Юникоде.  
  
 `TargetFileName`Атрибут также можно использовать для переименования файлов с параметрами. Следующая процедура описывает, как переименовать файл `MyFile.vb` , который находится в корневом каталоге файла Template. zip, в имя файла на основе имени проекта.  
  
### <a name="to-rename-files-with-parameters"></a>Переименование файлов с параметрами  
  
1. Используйте следующий код XML в VSTEMPLATE-файле:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2. Откройте файл проекта (VBPROJ для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] проекта) в текстовом редакторе или [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. В файле проекта поместите строку, похожую на следующий код XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4. Замените строку кода следующим XML-кодом:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     При создании проекта на основе этого шаблона имя файла будет основываться на имени пользователя, введенном в диалоговом окне **Новый проект** , при этом удаляются все незащищенные символы и пробелы. Дополнительные сведения см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для шаблона проекта [!INCLUDE[csprcs](../includes/csprcs-md.md)] приложения.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
