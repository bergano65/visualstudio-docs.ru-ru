---
title: Элемент Максфрамеворкверсион (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194326"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает максимальную версию .NET Framework, необходимую для шаблона. Он определяет, отображается ли шаблон в разделе **шаблоны** диалогового окна **Добавление нового проекта** на основе значения, выбранного в поле **Целевая версия платформы** в диалоговом окне **Добавление нового проекта** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в диалоговом окне " **Новый проект** " или " **Добавление нового элемента** ".|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Текст должен быть самым высоким номером версии .NET Framework, разрешенным шаблоном.  
  
## <a name="remarks"></a>Remarks  
 Параметр `MaxFrameworkVersion` является необязательным элементом. Элемент в `TemplateData` разделе VSTEMPLATE-файла выступает в качестве фильтра для раздела **шаблоны** диалогового окна **Добавление нового проекта** . Будут отображены только те шаблоны, требования .NET Framework которых меньше `MaxFrameworkVersion` значений элементов, в зависимости от значения, выбранного в поле **Целевая версия платформы** в диалоговом окне **Добавление нового проекта** . `MaxFrameworkVersion`Элемент следует опустить, если он не является обязательным, поэтому не следует случайно отображать шаблоны при их использовании в более новых версиях .NET Framework.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для стандартного [!INCLUDE[csprcs](../includes/csprcs-md.md)] шаблона класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 В этом примере максимальная версия .NET Framework, необходимая для шаблона, представленная `MaxFrameworkVersion` , — 3,5. Указанный выше шаблон будет отображаться, только если выбрано значение 3,0 или 3,5 в поле **Целевая версия платформы** в диалоговом окне **Добавление нового проекта** .  
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
