---
title: "Практическое руководство. Создание веб-шаблонов вручную | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шаблоны проектов [Visual Studio], Интернет"
  - "шаблоны [Visual Studio], Интернет"
  - "шаблоны Visual Studio, Интернет"
  - "веб-шаблоны [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Создание веб-шаблонов вручную
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создание веб\-шаблона отличается от создания других типов шаблонов.  Поскольку шаблоны веб\-проектов отображаются в диалоговом окне **Добавить новый веб\-сайт** и элементы веб\-проекта классифицируются по языку программирования, файл с расширением VSTEMPLATE должен указать шаблон в качестве веб\-шаблона и определить язык программирования.  
  
> [!NOTE]
>  Веб\-шаблоны должны содержать пустой файл с расширением WEBPROJ, который указан с помощью атрибута `File` элемента `Project`.  Хотя для веб\-проектов не требуются файлы проекта, этот файл необходим для обеспечения правильной работы веб\-шаблона.  
  
### Чтобы вручную создать веб\-шаблон  
  
1.  Создайте веб\-проект.  
  
2.  Измените или удалите файлы в проекте или добавьте новые файлы в проект.  
  
3.  Создайте новый XML\-файл и сохраните его, используя расширение имени файла VSTEMPLATE, в том же каталоге, где находится проект.  Не добавляйте его в проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Создайте XML\-файл .vstemplate для метаданных шаблона проекта.  Для получения дополнительных сведений см. пример в следующем разделе.  
  
5.  Найдите элемент `ProjectType` в файле .vstemplate и задайте текстовое значение `Web`.  
  
6.  После элемента `ProjectType` добавьте элемент `ProjectSubType` и задайте текстовое значение соответствующее языку программирования шаблона.  Язык программирования может иметь одно из следующих значений:  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Примеры.  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Выберите файлы в шаблоне \(включая файл с расширением VSTEMPLATE\), щелкните их правой кнопкой мыши, выберите **Отправить**, затем щелкните **Сжатая ZIP\-папка**.  Файлы упакуются в ZIP\-файл.  
  
8.  Поместите ZIP\-файл шаблона в каталог шаблонов проектов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  По умолчанию этот каталог \\Мои документы\\Visual Studio *номер версии*\\My Exported Templates\\.  
  
## Пример  
 В следующем примере показан базовый файл с расширением VSTEMPLATE для шаблона веб\-проекта.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)