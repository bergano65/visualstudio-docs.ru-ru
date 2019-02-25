---
title: Элемент ProjectType (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd369d68ae8f0e340787fadb0dafd43301fe3e62
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686214"
---
# <a name="projecttype-element-visual-studio-templates"></a>Элемент ProjectType (шаблоны Visual Studio)
Относит шаблон проекта, чтобы он отображался в указанной группе в **новый проект** или **Добавление нового элемента** диалоговое окно.

> [!WARNING]
>  Шаблоны проектов, поддерживаются для C++, начиная с Visual Studio 2012. Они не поддерживаются для C++ в Visual Studio 2010 и более ранних версий.

 \<VSTemplate > \<TemplateData > \<ProjectType >

## <a name="syntax"></a>Синтаксис

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Это значение указывает тип проекта, шаблон будет создан и должен содержать один из следующих значений:

- `CSharp`: Указывает, что этот шаблон создает [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта или элемента.

- `VisualBasic`: Указывает, что этот шаблон создает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] проекта или элемента.

- `Web`: Указывает, что этот шаблон создает веб-проекта или элемента. Если `ProjectType` элемент может содержать это значение, определенный на языке проекта или элемента в [элемент ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Примечания
 `ProjectType` — обязательный дочерний элемент элемента `TemplateData`.

 Значение `ProjectType` элемент указывает, где находится шаблон **новый проект** или **Добавление нового элемента** диалоговое окно. Например, шаблон с `ProjectType` значение `CSharp` подчеркивается **Visual C#** узел в **новый проект** диалоговое окно.

 Подтип шаблона можно указать с помощью [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) элемент.

## <a name="example"></a>Пример
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

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
            <ProjectItem>Form1.cs<ProjectItem>
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

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)