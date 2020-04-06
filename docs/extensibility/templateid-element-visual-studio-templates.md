---
title: Элемент TemplateID (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699059"
---
# <a name="templateid-element-visual-studio-templates"></a>Элемент TemplateID (шаблоны Visual Studio)
Уотек идентификатора шаблона элемента, который классифицируется в группу шаблонов элементов элементом элементом [элемента.](../extensibility/templategroupid-element-visual-studio-templates.md)

 \<VSTemplate \<> TemplateData> \<templateID>

## <a name="syntax"></a>Синтаксис

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 A, `string` представляющий идентификатор шаблона элемента, который классифицируется в группу шаблонов элементов элементом `TemplateGroupID` элементом.

## <a name="remarks"></a>Примечания
 Параметр `TemplateID` является необязательным элементом.

 Если файл «vstemplate» `TemplateID` опускает элемент, элемент [«Имя»](../extensibility/name-element-visual-studio-templates.md) используется в качестве идентификатора для шаблона.

 Значение `TemplateID` элемента используется вместе с регистрацией системы проекта (HKEY_LOCAL_MACHINE »SOFTWARE»Microsoft»VisualStudio »11.0 »Проекты)\\для фильтрации шаблонов, которые появляются в диалоговом окне **Добавления нового элемента.**

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
