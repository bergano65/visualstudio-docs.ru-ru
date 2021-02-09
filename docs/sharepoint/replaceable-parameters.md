---
title: Заменяемые параметры | Документация Майкрософт
description: Просмотрите заменяемые параметры (токены), которые задают значения в файлах проекта для элементов решения SharePoint, фактические значения которых не известны во время разработки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload: office
ms.openlocfilehash: 3eb6e737a1f939e05e6a6be7f2c9ba950fc411d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889503"
---
# <a name="replaceable-parameters"></a>Заменяемые параметры
  Заменяемые параметры (или *токены*) могут использоваться внутри файлов проекта для предоставления значений элементам решения SharePoint, фактические значения которых не известны во время разработки. Они похожи на [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] маркеры стандартных шаблонов. Дополнительные сведения см. в разделе [Параметры шаблона](../ide/template-parameters.md).

## <a name="token-format"></a>Формат токена
 Маркеры начинаются и заканчиваются знаком доллара ($). При развертывании все используемые токены заменяются фактическими значениями, если проект упакован в пакет решения SharePoint (*WSP* -файл). Например, токен **$SharePoint. Package.Name $** может разрешаться в строку "тестовый пакет SharePoint".

## <a name="token-rules"></a>Правила токенов
 К маркерам применяются следующие правила.

- Токены можно указывать в любом месте строки.

- Маркеры не могут охватывать несколько строк.

- Один и тот же токен можно указать более одного раза в одной и той же строке и в одном файле.

- В одной строке могут быть указаны разные токены.

  Токены, которые не соответствуют этим правилам, игнорируются и не приводят к появлению предупреждения или ошибки.

  Замена токенов по строковым значениям выполняется сразу после преобразования манифеста. Эта замена позволяет пользователю изменять шаблоны манифеста с помощью маркеров.

### <a name="token-name-resolution"></a>Разрешение имени токена
 В большинстве случаев маркер разрешается в определенное значение независимо от того, где оно содержится. Однако если маркер связан с пакетом или функцией, значение маркера зависит от того, где он содержится. Например, если компонент находится в пакете а, то маркер `$SharePoint.Package.Name$` разрешается в значение "пакет а". Если одна и та же функция находится в пакете B, то `$SharePoint.Package.Name$` разрешается в «Package B».

## <a name="tokens-list"></a>Список токенов
 В следующей таблице перечислены доступные токены.

|Имя|Описание|
|----------|-----------------|
|$SharePoint. Project. FileName $|Имя содержащего файла проекта, например *невпрож. csproj*.|
|$SharePoint. Project. Филенамевисаутекстенсион $|Имя содержащего файла проекта без расширения имени файла. Например, "Невпрож".|
|$SharePoint. Project. AssemblyFullName $|Отображаемое имя (строгое имя) выходной сборки содержащего проекта.|
|$SharePoint. Project. Ассемблифиленаме $|Имя выходной сборки содержащего проекта.|
|$SharePoint. Project. Ассемблифиленамевисаутекстенсион $|Имя выходной сборки содержащего проекта без расширения имени файла.|
|$SharePoint. Project. Ассемблипубликкэйтокен $|Токен открытого ключа выходной сборки содержащего проекта, преобразованный в строку. (16 символов в шестнадцатеричном формате «x2»).|
|$SharePoint. Package.Name $|Имя содержащего пакета.|
|$SharePoint. Package. имя_файла $|Имя файла определения содержащего пакета.|
|$SharePoint. Package. Филенамевисаутекстенсион $|Имя файла определения содержащего пакета (без расширения).|
|$SharePoint. Package.Id $|ИДЕНТИФИКАТОР SharePoint для содержащего пакета. Если функция используется в нескольких пакетах, это значение изменится.|
|$SharePoint. feature. имя_файла $|Имя файла определения содержащего компонента, например *Feature1. Feature*.|
|$SharePoint. feature. Филенамевисаутекстенсион $|Имя файла определения компонента без расширения имени файла.|
|$SharePoint. feature. Деплойментпас $|Имя папки, содержащей компонент в пакете. Этот маркер соответствует свойству "путь развертывания" в конструкторе компонентов. Пример значения: "Project1_Feature1".|
|$SharePoint. Feature.Id $|ИДЕНТИФИКАТОР SharePoint содержащего его компонента. Этот маркер, как и для всех маркеров уровня компонентов, может использоваться только файлами, включенными в пакет с помощью функции, которая не добавляется непосредственно в пакет за пределами компонента.|
|$SharePoint. ProjectItem.Name $|Имя элемента проекта (не имя файла), полученное из **ISharePointProjectItem.Name**.|
|$SharePoint \<GUID> . Type.. AssemblyQualifiedName $|Имя типа, включающее наименование сборки и соответствующее идентификатору [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] токена. Идентификатор [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] задается символами в нижнем регистре в формате, аналогичном формату Guid.ToString("D") (т. е. "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx").|
|$SharePoint \<GUID> . Type.. FullName $|Полное имя типа, совпадающее с идентификатором GUID в токене. Формат GUID имеет нижний регистр и соответствует формату GUID. ToString ("D") (то есть xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Добавление расширений в список расширений файлов для замещения токена
 Хотя маркеры теоретически могут использоваться любым файлом, принадлежащим элементу проекта SharePoint, включенному в пакет, по умолчанию [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ищет маркеры только в файлах пакета, файлах манифеста и файлах со следующими расширениями:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- СВИДЕТЕЛЬСТВО

- ASPX

- WebPart

- DWP

  Эти расширения определяются `<TokenReplacementFileExtensions>` элементом в файле Microsoft. VisualStudio. SharePoint. targets, расположенном в папке... \\<Program Files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  Однако можно добавить дополнительные расширения файлов в список. Добавьте `<TokenReplacementFileExtensions>` элемент в любой PropertyGroup в файле проекта SharePoint, который определен перед \<Import> файлом целевых объектов SharePoint.

> [!NOTE]
> Поскольку замена токенов происходит после компиляции проекта, не следует добавлять расширения файлов для компилируемых типов файлов, таких как *CS*, *VB* или *RESX*. Маркеры заменяются только в файлах, которые не компилируются.

 Например, чтобы добавить расширения имен файлов (*. мекстенсион* и *. йоурекстенсион*) в список расширений имени файла для замены токенов, добавьте следующий код в файл проекта (с *расширением CSPROJ*):

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

 Расширение можно добавить непосредственно в целевые файлы (*Targets*). Однако добавление расширения приводит к изменению списка расширений для всех проектов SharePoint, упакованных в локальную систему, а не только собственного. Это расширение может быть удобно, если вы являетесь единственным разработчиком в системе или если это требуется большинству проектов. Однако, поскольку он зависит от системы, этот подход не является переносимым, поэтому рекомендуется добавлять расширения в файл проекта.

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
