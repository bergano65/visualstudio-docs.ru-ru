---
title: "Подстановочные параметры | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "подстановочные параметры [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, подстановочные параметры"
  - "разработка приложений SharePoint в Visual Studio, лексемы"
  - "токены [разработка приложений SharePoint в Visual Studio]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Подстановочные параметры
  Подстановочные параметры \(или *токены*\) можно использовать в файлах проекта для представления значений элементов решения SharePoint, фактические значения которых неизвестны во время разработки.  Они действуют аналогично стандартным маркерам шаблонов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Для получения дополнительной информации см. [Параметры шаблона](../ide/template-parameters.md).  
  
## Формат токенов  
 Токены начинаются и заканчиваются знаком доллара \($\).  Все используемые токены заменяются фактическими значениями при записи проекта в WSP\-файл пакета решения SharePoint во время развертывания.  Например, токен **$SharePoint.Package.Name$** может разрешаться в строку "Тестовый пакет SharePoint".  
  
## Правила токенов  
 В отношении токенов действуют следующие правила.  
  
-   Токены можно помещать в любом месте строки.  
  
-   Токен не может занимать несколько строк.  
  
-   Один и тот же токен может использоваться несколько раз в одной строке и в одном файле.  
  
-   В одной строке могут использоваться различные токены.  
  
 Токены, не соответствующие этим правилам, игнорируются, при этом не выдаются предупреждения и сообщения об ошибках.  
  
 Замена токенов значениями строки выполняется немедленно после преобразования манифеста, что позволяет использовать токены в шаблонах манифестов, отредактированных пользователем.  
  
### Разрешение имен токенов  
 В большинстве случаев токен разрешается в конкретное значение независимо от того, где он содержится.  Однако если токен относится к пакету или компоненту, значение токена зависит от того, где он содержится.  Например, если компонент находится в пакете А, токен `$SharePoint.Package.Name$` разрешается в значение "Пакет А". Если тот же компонент находится в пакете Б, токен `$SharePoint.Package.Name$` разрешается в "Пакет Б".  
  
## Список токенов  
 В следующей таблице перечислены доступные токены.  
  
|Имя|Описание|  
|---------|--------------|  
|$SharePoint.Project.FileName$|Имя файла содержащего проекта, например NewProj.csproj.|  
|$SharePoint.Project.FileNameWithoutExtension$|Имя файла содержащего проекта без расширения.  Например, "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Отображаемое имя \(строгое имя\) выходной сборки содержащего проекта.|  
|$SharePoint.Project.AssemblyFileName$|Имя выходной сборки содержащего проекта.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Имя выходной сборки содержащего проекта без расширения.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Токен открытого ключа выходной сборки содержащего проекта, преобразованный в строку. \(16 символов, шестнадцатеричный формат "x2"\).|  
|$SharePoint.Package.Name$|Имя содержащего пакета.|  
|$SharePoint.Package.FileName$|Имя файла определения содержащего пакета.|  
|$SharePoint.Package.FileNameWithoutExtension$|Имя \(без расширения\) файла определения содержащего пакета.|  
|$SharePoint.Package.Id$|Идентификатор SharePoint для содержащего пакета.  Если компонент используется в нескольких пакетах, это значение меняется.|  
|$SharePoint.Feature.FileName$|Имя файла определения содержащего компонента, например Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Имя файла определения компонента без расширения.|  
|$SharePoint.Feature.DeploymentPath$|Имя папки, содержащей компонент в пакете.  Этот токен соответствует свойству "Путь развертывания" в конструкторе компонентов.  Пример значения — Project1\_Feature1.|  
|$SharePoint.Feature.Id$|Идентификатор SharePoint содержащего компонента.  Этот токен \(как и все токены на уровне компонентов\) может использоваться только в файлах, включенных в пакет с помощью компонента, а не добавленных в пакет напрямую, вне компонента.|  
|$SharePoint.ProjectItem.Name$|Имя элемента проекта \(не имя файла\) в том виде, в каком оно было получено из **ISharePointProjectItem.Name**.|  
|$SharePoint.Type.\<GUID\>.AssemblyQualifiedName$|Имя типа, указанное относительно сборки и соответствующее идентификатору [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] маркера.  Формат [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] задается символами в нижнем регистре и соответствует формату Guid.ToString\("D"\) \(т. е. "xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx"\).|  
|$SharePoint.Type.\<GUID\>.FullName$|Полное имя типа, соответствующее идентификатору GUID в токене.  Идентификатор GUID задается символами в нижнем регистре в формате, аналогичном формату Guid.ToString\("D"\) \(т. е. "xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx"\).|  
  
## Добавление расширений в список расширений файлов, в которых выполняется замена токенов  
 Теоретически токены можно использовать в любом файле, который принадлежит к элементу проекта SharePoint, включенному в пакет, однако по умолчанию [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняет поиск токенов только в файлах пакета, файлах манифеста и файлах со следующими расширениями.  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX;  
  
-   ASPX;  
  
-   Webpart;  
  
-   DWP.  
  
 Эти расширения определены в элементе `<TokenReplacementFileExtensions>` в файле Microsoft.VisualStudio.SharePoint.targets, расположенном в папке …\\\<program files\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools.  
  
 Впрочем, в этот список можно добавить дополнительные расширения файлов.  Для этого нужно добавить элемент `<TokenReplacementFileExtensions>` в любую группу свойств в файле проекта SharePoint, определенном перед \<импортом\> файла целевых объектов SharePoint.  
  
> [!NOTE]  
>  Поскольку замена токенов осуществляется после компиляции проекта, не следует добавлять расширения для скомпилированных типов файлов, таких как CS, VB или RESX.  Токены заменяются только в нескомпилированных файлах.  
  
 Например, чтобы добавить расширения имен файлов ".myextension" и ".yourextension" в список расширений имен файлов, в которых заменяются токены, необходимо добавить в CSPROJ\-файл следующий код.  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Или же можно добавить расширение непосредственно в файл TARGETS.  Впрочем, в результате изменится список расширений для всех проектов SharePoint, размещенных на локальной системе, а не для отдельно взятого проекта.  Этой возможностью имеет смысл пользоваться, если в системе работает только один разработчик или если это требуется для большинства проектов.  Рекомендуется добавлять расширения в файл проекта, поскольку вышеописанный подход действует только в определенных системах и возможности его переноса ограничены.  
  
## См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  