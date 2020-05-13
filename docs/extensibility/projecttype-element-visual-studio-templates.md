---
title: Элемент ProjectType (Шаблоны визуальной студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701806"
---
# <a name="projecttype-element-visual-studio-templates"></a>Элемент ProjectType (шаблоны Visual Studio)
Категоризирует шаблон проекта таким образом, чтобы он отосвобождался в указанной группе в **new Project** или добавил диалоговую коробку **New Item.**

> [!WARNING]
> Шаблоны проекта поддерживаются для СЗ, начиная с Visual Studio 2012. Они не поддерживаются для C » в Visual Studio 2010 и более ранних версиях.

 \<VSTemplate \<> TemplateData> \<ProjectType>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Это значение определяет тип проекта, который создаст шаблон, и должно содержать одно из следующих значений:

- `CSharp`: Упомянет, что [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблон создает проект или элемент.

- `VisualBasic`: Упомянет, что [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] шаблон создает проект или элемент.

- `Web`: Упомянет, что шаблон создает веб-проект или элемент. Если `ProjectType` элемент содержит это значение, язык проекта или элемента определяется в [элементе ProjectSubType (Visual Studio Templates).](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="remarks"></a>Примечания
 `ProjectType` — обязательный дочерний элемент элемента `TemplateData`.

 Значение `ProjectType` элемента определяет, где шаблон находится в **новом проекте** или **добавить new Item** диалоговое окно. Например, шаблон со `ProjectType` значением `CSharp` отображается под узлом **Visual C'в** диалоговом поле Нового **Проекта.**

 Подтип шаблона можно указать с помощью элемента [ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="example"></a>Пример
 В следующем примере показаны метаданные [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] для шаблона проекта для приложения.

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
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectSubType (шаблоны Визуальной студии)](../extensibility/projectsubtype-element-visual-studio-templates.md)
