---
title: Подстановочные параметры | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: e79442ea42583f326f9cb59360777269c399b7a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879302"
---
# <a name="replaceable-parameters"></a>Подстановочные параметры
  Подстановочные параметры или *маркеры*, можно использовать в файлах проекта для предоставления значений для элементов решения SharePoint, фактические значения не известен во время разработки. Они в функции аналогичны стандарте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] токенам шаблонов. Дополнительные сведения см. в разделе [параметров шаблона](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Формат маркера
 Токены начинаются и заканчиваются символом доллара ($). В развертывании, все используемые токены заменяются фактическими значениями при упаковки проекта в пакет решения SharePoint (*.wsp* файла). Например, маркер **$SharePoint.Package.Name$** может разрешаться в строку «Тестовый пакет SharePoint».  
  
## <a name="token-rules"></a>Правила токенов
 Для маркеров, применяются следующие правила:  
  
- Маркеры можно указать в любом месте в строке.  
  
- Токен не может занимать несколько строк.  
  
- Тот же токен можно составить более одного раза в той же строке и в одном файле.  
  
- Различные маркеры могут быть указаны в той же строке.  
  
  Маркеры, которые не соответствует этим правилам учитываются, а не к возникновению предупреждения или ошибки.  
  
  Замена токенов значениями строки выполняется немедленно после преобразования манифеста. Такая замена позволяет пользователю изменять манифеста шаблонов с помощью маркеров.  
  
### <a name="token-name-resolution"></a>Разрешение имен токенов
 В большинстве случаев токен разрешается конкретное значение независимо от того, где он содержится. Тем не менее если маркер относится к пакета или компонента, значение токена зависит от которых он содержится. Например, если функция пребывает в пакет, токен `$SharePoint.Package.Name$` разрешается в значение «Пакет A.» Если тот же компонент находится в пакете Б, затем `$SharePoint.Package.Name$` разрешается в «Пакет B.»  
  
## <a name="tokens-list"></a>Список токенов
 В следующей таблице перечислены доступные токены.  
  
|name|Описание|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Например, файла проекта, содержащего имя *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Имя файла проекта, содержащего без расширения имени файла. Например, «NewProj».|  
|$SharePoint.Project.AssemblyFullName$|Отображаемое имя (строгое имя), содержащего проекта выходной сборки.|  
|$SharePoint.Project.AssemblyFileName$|Имя проекта, содержащего выходной сборки.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Имя проекта, содержащего выходной сборки, без расширения имени файла.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Токен открытого ключа, содержащего проекта выходной сборки, преобразуется в строку. (16 символов «x2» шестнадцатеричном формате.)|  
|$SharePoint.Package.Name$|Имя пакета.|  
|$SharePoint.Package.FileName$|Имя файла определения содержащего пакета.|  
|$SharePoint.Package.FileNameWithoutExtension$|Имя файла определения содержащего пакета (без расширения).|  
|$SharePoint.Package.Id$|Идентификатор пакета SharePoint. Если компонент используется в нескольких пакетах, это значение будет изменено.|  
|$SharePoint.Feature.FileName$|Имя файла определения, содержащего условия, например *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Имя файла определения функции, без расширения имени файла.|  
|$SharePoint.Feature.DeploymentPath$|Имя папки, которая содержит компонент в пакет. Этот токен соответствует свойству «Путь развертывания» в конструкторе компонентов. Например, значение — «Project1_Feature1».|  
|$SharePoint.Feature.Id$|Идентификатор SharePoint, содержащего компонента. Этот маркер, как с помощью всех маркеров функциональным уровнем, может использоваться только в файлах, включенных в пакет с помощью компонента, не добавил напрямую в пакет вне компонента.|  
|$SharePoint.ProjectItem.Name$|Имя элемента проекта (не имя файла), как получено из **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Имя типа, включающее наименование сборки и соответствующее идентификатору [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] токена. Идентификатор [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] задается символами в нижнем регистре в формате, аналогичном формату Guid.ToString("D") (т. е. "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx").|  
|$SharePoint.Type. \<GUID >. FullName$|Полное имя типа, соответствующее идентификатору GUID в токене. Формат идентификатора GUID, производится в нижнем регистре и аналогичном формату Guid.ToString("D") (т. е xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Добавление расширений в список расширений файлов замена токенов
 Несмотря на то, что теоретически токены можно использовать в любом файле, к которой принадлежит проект SharePoint, элемент включен в пакет, по умолчанию, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняет поиск токенов только в файлы пакета, файлы и файлы, имеющие следующие расширения:  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Веб-части  
  
- DWP  
  
  Эти расширения определяются `<TokenReplacementFileExtensions>` элемент в файле Microsoft.VisualStudio.SharePoint.targets, расположенный в... \\< программные файлы\>папок \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.  
  
  Тем не менее, можно добавить дополнительные расширения файлов в список. Добавить `<TokenReplacementFileExtensions>` элемент в любую группу свойств в файле проекта SharePoint, который определяется перед \<импорта > файла целевых объектов SharePoint.  
  
> [!NOTE]  
>  Так как замена токенов происходит после компиляции проекта, не следует добавлять расширения для типов файлов, которые компилируются, такие как *.cs*, *.vb* или *.resx*. Токены заменяются только в файлах, которые не компилируются.  
  
 Например, чтобы добавить расширения имен файлов (*.myextension* и *.yourextension*) в список расширений имен файлов замена токенов, необходимо добавить следующую команду, чтобы проект (*.csproj* ) файл:  
  
```xml  
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
  
 Можно добавить расширение непосредственно к целевым объектам (*.targets*) файла. Тем не менее, добавив расширение изменяет список расширений для всех проектов SharePoint, размещенных в локальной системе, а не только свои собственные. Это расширение может быть удобным при единственный разработчик в системе, или если это требуется для большинства проектов. Тем не менее это характерные для системы, такой подход не является переносимым и таким образом, рекомендуется, вы добавляете каких-либо расширений к файлу проекта, вместо этого.  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
