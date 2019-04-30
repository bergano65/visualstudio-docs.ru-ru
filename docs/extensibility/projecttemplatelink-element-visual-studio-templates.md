---
title: Элемент ProjectTemplateLink (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc253967cf4f52d6e958b8b092f44f753bac2e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805952"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Элемент ProjectTemplateLink (шаблоны Visual Studio)
Указывает путь к *.vstemplate* файлу для одного проекта в многопроектном шаблоне.

 \<VSTemplate > \<TemplateContent > \<ProjectCollection > \<ProjectTemplateLink > - или - \<VSTemplate > \<TemplateContent > \<ProjectCollection > \<SolutionFolder > \<ProjectTemplateLink >

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
|`ProjectName`|Необязательный атрибут.<br /><br /> Задает имя каждого отдельного проекта в многопроектном шаблоне. **Новый проект** диалоговое окно не может присваивать имена отдельным проектам.|
|`CopyParameters`|Включает копирование всех переменных в шаблоне основной группы в каждый из связанных шаблонов.<br /><br /> Параметры в связанных шаблонах имеют префикс `"$ext_*$"`. Например, если в шаблоне родительской группы параметр `$projectname$` имеет значение **ExampleProject1**, когда связанный шаблон возвращает своей очереди, который будет выполнен, он получает параметр `$ext_projectname$`, который является копией `$projectname$`параметра в шаблоне родительской группы.<br /><br /> Это позволяет связанным шаблонам совместно использовать некоторые общие параметры, которые можно удобным образом создавать в шаблоне родительской группы.<br /><br /> Этот атрибут является необязательным и для него автоматически устанавливается значение по умолчанию `false`, если он не включен.<br /><br /> Представлено в обновлении 2 для Visual Studio 2013. Чтобы сослаться на правильной версии продукта, см. в разделе [ссылки на сборки, представленные в Visual Studio 2013 SDK с обновлением 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Группирует проекты в многопроектных шаблонах.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст указывает путь к *.vstemplate* файла шаблона.

## <a name="remarks"></a>Примечания
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. `ProjectTemplateLink` Элемент используется, чтобы указать расположение *.vstemplate* файл для одного из проектов в этом шаблоне. *.Vstemplate* файл многопроектного шаблона содержит один `ProjectTemplateLink` элемент для каждого проекта в шаблоне. Дополнительные сведения о многопроектных шаблонах см. в разделе [как: Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Пример
 В этом примере показан простой корневой многопроектных *.vstemplate* файл. В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту. Если `ProjectName` атрибут не существует, имя *.vstemplate* файл используется в качестве имени проекта.

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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)