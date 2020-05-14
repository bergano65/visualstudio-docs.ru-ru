---
title: Элемент сборки (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740043"
---
# <a name="assembly-element-visual-studio-templates"></a>Элемент сборки (шаблоны Visual Studio)
Определяет информацию о сборке, которую шаблон использует для добавления ссылки этой сборки на проекты.

 \<VSTemplate \<> TemplateContent \<> \<ссылки> ссылки> \<ассамблеи>

## <a name="syntax"></a>Синтаксис

```
<Assembly> AssemblyName </Assembly>
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
|[Справочник](../extensibility/reference-element-visual-studio-templates.md)|Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 В этом тексте указывается сборка для добавления в проект при мгновенном воспроизведении шаблона элемента. Это название сборки должно быть указано одним из следующих способов:

- Как полное название сборки. Пример:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Как простая текстовая ссылка. Пример:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Примечания
 `Assembly` — обязательный дочерний элемент элемента `Reference`.

 `Reference`Элементы `References,` `Assembly` и элементы могут использоваться только в `Type` файлах `Item` *.vstemplate,* которые имеют значение атрибута.

## <a name="example"></a>Пример
 Следующий пример иллюстрирует `TemplateContent` элемент шаблона элемента. Это XML добавляет ссылки на *System.dll* и *System.Data.dll* сборки.

```
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
