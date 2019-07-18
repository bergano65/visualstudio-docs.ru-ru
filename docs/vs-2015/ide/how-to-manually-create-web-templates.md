---
title: Практическое руководство. Создание веб-шаблонов вручную | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8a505fe3428a8e16c321eee4764f8a62fff65511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431104"
---
# <a name="how-to-manually-create-web-templates"></a>Практическое руководство. Создание веб-шаблонов вручную
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создание веб-шаблона отличается от создания других типов шаблонов. Так как шаблоны веб-проектов отображаются в диалоговом окне **Добавить новый веб-сайт**, а элементы веб-проекта классифицируются по языку программирования, файл VSTEMPLATE должен указывать, что это веб-шаблон, а также задавать язык программирования.  
  
> [!NOTE]
> Веб-шаблоны должны содержать пустой файл WEBPROJ, указанный с помощью атрибута `File` элемента `Project`. Хотя веб-проектам не нужны файлы проекта, этот файл необходим для правильной работы веб-шаблона.  
  
### <a name="to-manually-create-a-web-template"></a>Создание веб-шаблонов вручную  
  
1. Создайте веб-проект.  
  
2. Измените или удалите файлы в проекте или добавьте в него новые файлы.  
  
3. Создайте XML-файл и сохраните его, используя расширение VSTEMPLATE, в одном каталоге с проектом. Не добавляйте его в проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Создайте VSTEMPLATE-файл с XML-кодом, чтобы предоставить метаданные шаблона проекта. Дополнительные сведения см. в примере в следующем разделе.  
  
5. Найдите в VSTEMPLATE-файле элемент `ProjectType` и задайте `Web` в качестве текстового значения.  
  
6. После элемента `ProjectType` добавьте элемент `ProjectSubType` и задайте язык программирования этого шаблона в качестве текстового значения. Этот язык программирования может принимать одно из следующих значений:  
  
   - CSharp  
  
   - VisualBasic  
  
     Пример:  
  
   ```  
   <TemplateData>  
       ...  
       <ProjectType>Web</ProjectType>  
       <ProjectSubType>CSharp</ProjectSubType>  
       ...  
   </TemplateData>  
   ```  
  
7. Выберите файлы в шаблоне (включая VSTEMPLATE-файл), щелкните их правой кнопкой мыши, выберите пункт **Отправить**, а затем **Сжатая ZIP-папка**. Файлы сжимаются в ZIP-файл.  
  
8. Поместите ZIP-файл шаблона в каталог шаблонов проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. По умолчанию это каталог \My Documents\Visual Studio *версия*\My Exported Templates\\.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает базовый VSTEMPLATE-файл для шаблона веб-проекта.  
  
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
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
