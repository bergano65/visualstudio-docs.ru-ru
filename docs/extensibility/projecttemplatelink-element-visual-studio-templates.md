---
title: Элемент ProjectTemplateLink (Визуальная студия шаблонов) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701824"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Элемент ProjectTemplateLink (шаблоны Visual Studio)
Онажай путь к файлу *.vstemplate* одного проекта в шаблоне мультипроектов.

 \<VSTemplate \<> \<TemplateContent> \<ProjectCollection> \<ProjectTemplateLink \<>-или- VSTemplate> TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Синтаксис

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`ProjectName`|Необязательный атрибут.<br /><br /> Задает имя каждого отдельного проекта в многопроектном шаблоне. Диалоговая коробка **Нового проекта** не может присваивать имена отдельным проектам.|
|`CopyParameters`|Включает копирование всех переменных в шаблоне основной группы в каждый из связанных шаблонов.<br /><br /> Параметры в связанных шаблонах имеют префикс `"$ext_*$"`. Например, если в шаблоне `$projectname$` родительской группы параметр имеет значение **ExampleProject1,** когда связанный шаблон `$ext_projectname$`получает свою очередь, `$projectname$` чтобы быть выполнены, он приобретает параметр, который является копией параметра из шаблона родительской группы.<br /><br /> Это позволяет связанным шаблонам совместно использовать некоторые общие параметры, которые можно удобным образом создавать в шаблоне родительской группы.<br /><br /> Этот атрибут является необязательным и для него автоматически устанавливается значение по умолчанию `false`, если он не включен.<br /><br /> Представлено в обновлении 2 для Visual Studio 2013. Для ссылки на правильную версию продукта, см [Справочник сборки доставлены в Visual Studio 2013 SDK Обновление 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Группирует проекты в многопроектных шаблонах.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 В этом тексте оговаривается путь к файлу *шаблона .vstemplate.*

## <a name="remarks"></a>Примечания
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. Элемент `ProjectTemplateLink` используется для определения местоположения файла *.vstemplate* для одного из проектов в шаблоне. Файл *«vstemplate»* шаблона мультипроекта `ProjectTemplateLink` содержит один элемент для каждого проекта в шаблоне. Для получения дополнительной информации о многопроектных шаблонах [см.](../ide/how-to-create-multi-project-templates.md)

## <a name="example"></a>Пример
 Этот пример показывает простой файл многопроектного *корня .vstemplate.* В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту. Если `ProjectName` атрибут не существует, имя файла *.vstemplate* используется в качестве имени проекта.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Как: Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)
