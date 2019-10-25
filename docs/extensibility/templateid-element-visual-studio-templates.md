---
title: Элемент TemplateID (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718742"
---
# <a name="templateid-element-visual-studio-templates"></a>Элемент TemplateID (шаблоны Visual Studio)
Задает идентификатор для шаблона элемента, разбитого по категориям в группе шаблонов элементов с помощью элемента [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate > \<TemplateData > \<TemplateID >

## <a name="syntax"></a>Синтаксис

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 @No__t_0, представляющий идентификатор шаблона элемента, отнесенный к группе шаблонов элементов по элементу `TemplateGroupID`.

## <a name="remarks"></a>Заметки
 `TemplateID` — это необязательный элемент.

 Если VSTEMPLATE-файл пропускает элемент `TemplateID`, то в качестве идентификатора шаблона используется элемент [Name](../extensibility/name-element-visual-studio-templates.md) .

 Значение элемента `TemplateID` используется вместе с регистрацией системы проекта (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\) для фильтрации шаблонов, которые отображаются в диалоговом окне **Добавление нового элемента** .

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)