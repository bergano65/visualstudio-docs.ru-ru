---
title: Справочный элемент (Visual Studio Шаблоны) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701627"
---
# <a name="reference-element-visual-studio-templates"></a>Справочный элемент (шаблоны Visual Studio)
Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.

 \<VSTemplate \<> TemplateContent \<> \<ссылки> справочные>

## <a name="syntax"></a>Синтаксис

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Сборки](../extensibility/assembly-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет информацию о сборке, которую шаблон использует для добавления ссылки этой сборки на проекты. В каждом `Reference` `Assembly` элементе должен быть один элемент.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Ссылки](../extensibility/references-element-visual-studio-templates.md)|Группирует ссылки сборки, которые шаблон добавляет в проекты.|

## <a name="remarks"></a>Примечания
 `Reference` — обязательный дочерний элемент элемента `References`.

 `Reference` Элементы `References` и элементы могут быть использованы `Type` только в `Item`файлах *.vstemplate,* которые имеют значение атрибута.

## <a name="example"></a>Пример
 Следующий пример иллюстрирует `TemplateContent` элемент шаблона элемента. Это XML добавляет ссылки на *System.dll* и *System.Data.dll* сборки.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
