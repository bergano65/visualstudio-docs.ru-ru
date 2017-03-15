---
title: "Элемент ProjectItem (шаблоны проектов Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> - элемент [шаблоны проектов Visual Studio]"
  - "ProjectItem - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Элемент ProjectItem (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает файла, который включается в шаблон проекта.  
  
> [!NOTE]
>  Элемент `ProjectItem` принимает различные атрибуты в зависимости от того, для чего предназначен шаблон \(для проекта или элемента\).  В этом разделе объясняется использование элемента `ProjectItem` для шаблонов проектов.  Описание элемента `ProjectItem` для шаблонов элементов содержится в разделе [Элемент ProjectItem \(шаблоны элементов Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
## Синтаксис  
  
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
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Указывает путь и имя элемента проекта при создании проекта из шаблона.  Этот атрибут полезен для создания структуры каталогов, отличающейся от структуры каталогов в ZIP\-файле шаблона, а также для использования замены параметров для создания имени элемента.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, имеются ли в элементе значения параметров, которые должны быть заменены при создании проекта из шаблона.  Значение по умолчанию — `false`.|  
|`OpenInEditor`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, требуется ли открывать элемент в соответствующем редакторе или в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при создании проекта из шаблона.<br /><br /> Атрибуты `OpenInWebBrowser` и `OpenInHelpBrowser` игнорируются для элемента, имеющего атрибут `OpenInEditor` со значением `true`.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInWebBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, требуется ли открывать элемент в браузере при создании проекта из шаблона.<br /><br /> В браузере можно открывать только HTML\-файлы и текстовые файлы, являющиеся локальными по отношению к проекту.  Внешние URL\-адреса нельзя открывать с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenInHelpBrowser`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, требуется ли открывать элемент в средстве просмотра справки при создании проекта из шаблона.<br /><br /> В средстве просмотра справки можно открывать только HTML\-файлы и текстовые файлы, являющиеся локальными по отношению к проекту.  Внешние URL\-адреса нельзя открывать с помощью этого атрибута.<br /><br /> Значение по умолчанию — `false`.|  
|`OpenOrder`|Необязательный атрибут.<br /><br /> Указывает числовое значение, представляющее порядок, используемый для открытия элементов в соответствующих редакторах.  Все значения должны быть кратными 10.  Элементы с более высокими значениями `OpenOrder` открываются в первую очередь.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Проект](../extensibility/project-element-visual-studio-templates.md)|Указывает файлы или каталоги, которые будут добавлены в проект.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Строка `string`, представляющая путь к файлу или имя файла в ZIP\-файле шаблона.  
  
## Заметки  
 `ProjectItem` является необязательным дочерним элементом `Project`.  
  
 Атрибут `TargetFileName` может использоваться для создания структуры каталогов, отличающейся от структуры каталогов в ZIP\-файле шаблона.  Например, если файл `MyFile.vb` находится в корне ZIP\-файла шаблона, но его необходимо поместить в каталог `CustomFiles` во всех проектах, созданных из шаблона, нужно использовать следующий XML\-код.  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Атрибут `TargetFileName` также можно использовать для переименования файлов, в именах которых содержатся буквы национальных алфавитов.  Например, ZIP\-файл шаблона не может содержать имена файлов с символами Юникода, поэтому такие файлы необходимо переименовывать перед сжатием в ZIP\-файл.  Атрибут `TargetFileName` можно использовать для возвращения файлу оригинального имени с символами Юникода.  
  
 Атрибут `TargetFileName` также можно использовать для переименования файлов с параметрами.  В следующей процедуре объясняется, как переименовать файл `MyFile.vb`, существующий в корневом каталоге ZIP\-файла шаблона, и задать ему имя, основывающееся на имени проекта.  
  
### Переименование файлов с параметрами  
  
1.  Используйте в VSTEMPLATE\-файле следующий XML\-код.  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Откройте файл проекта \(VBPROJ\-файл для проекта [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) в текстовом редакторе или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  В файле проекта найдите строку, похожую на следующий XML\-код.  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Замените строку кода следующим XML\-кодом.  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Когда из этого шаблона создается элемент, имя файла будет основываться на имени, введенном пользователем в диалоговом окне **Создать проект**, с удалением всех небезопасных знаков и пробелов.  Дополнительные сведения см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
## Пример  
 В следующем примере демонстрируются метаданные для шаблона проекта приложения [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Элемент ProjectItem \(шаблоны элементов Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)