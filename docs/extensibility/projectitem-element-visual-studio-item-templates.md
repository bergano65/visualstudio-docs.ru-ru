---
title: ProjectItem Элемент (Visual Studio Элемент шаблоны) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701865"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Элемент ProjectItem (шаблоны элементов Visual Studio)
Упогоняет файл, включенный в шаблон элемента.

> [!NOTE]
> Элемент `ProjectItem` принимает различные атрибуты в зависимости от того, является ли шаблон для проекта или элемента. Эта тема `ProjectItem` объясняет элемент для элемента. Для объяснения `ProjectItem` элемента для шаблонов проекта см. [ProjectItem element (Visual Studio project templates)](../extensibility/projectitem-element-visual-studio-project-templates.md)

 \<VSTemplate \<> TemplateContent> \<projectItem>

## <a name="syntax"></a>Синтаксис

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|---------------------| - |
| `SubType` | Необязательный атрибут.<br /><br /> Обрасьте подтип элемента в шаблоне нескольких файлового элемента. Это значение используется для определения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора, который будет использоваться для открытия элемента. |
| `CustomTool` | Необязательный атрибут.<br /><br /> Устанавливает CustomTool для элемента в файле проекта. |
| `ItemType` | Необязательный атрибут.<br /><br /> Устанавливает ItemType для элемента в файле проекта. |
| `ReplaceParameters` | Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, имеет ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию: `false`. |
| `TargetFileName` | Необязательный атрибут.<br /><br /> Упоняет имя элемента, созданного из шаблона. Этот атрибут полезен для использования замены параметров для создания имени элемента. |

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Определяет содержимое шаблона.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 A, `string` представляющий имя файла в файле *шаблона .zip.*

## <a name="remarks"></a>Примечания
 `ProjectItem`является необязательным `TemplateContent`ребенком .

 Атрибут `TargetFileName` может быть использован для переименования файлов с параметрами. Например, если файл *MyFile.vb* существует в корневом каталоге файла *шаблона .zip,* но вы хотите, чтобы файл был назван на основе имени файла, предоставленного пользователем в диалоговом окне **Добавления нового элемента,** вы будете использовать следующий XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Когда элемент создается из этого шаблона, имя файла будет основываться на имени пользователя, вписавшем в диалоговое окно **Добавить новый элемент.** Это полезно при создании многофайловых шаблонов элементов. Для получения дополнительной информации [см. Как: Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [параметров шаблона.](../ide/template-parameters.md)

## <a name="example"></a>Пример
 Следующий пример иллюстрирует метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона элементов для класса.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)
- [Параметры шаблона](../ide/template-parameters.md)
