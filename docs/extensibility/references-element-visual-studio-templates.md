---
title: Ссылается на элемент (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ae0ee308af1502a7c07766e790b79e51f692a96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433413"
---
# <a name="references-element-visual-studio-templates"></a>Элемент References (шаблоны Visual Studio)
Группы, которые добавляются в проекты ссылки на сборки.

 \<VSTemplate > \<TemplateContent > \<ссылки >

## <a name="syntax"></a>Синтаксис

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект. Должен быть один или несколько `Reference` элементов в `References` элемент.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|

## <a name="remarks"></a>Примечания
 `References` — необязательный дочерний элемент элемента `TemplateContent`.

 `Reference` И `References` элементы могут использоваться только в *.vstemplate* файлы, имеющие `Type` значение атрибута `Item`.

## <a name="example"></a>Пример
 В следующем примере показано `TemplateContent` элемент шаблона элемента. Этот XML-код добавляет ссылки на *System.dll* и *System.Data.dll* сборок.

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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
