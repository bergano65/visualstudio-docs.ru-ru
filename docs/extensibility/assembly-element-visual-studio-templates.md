---
title: Элемент ASSEMBLY (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13c52b7f913e35ace3e0fd41227e27b6c00e90e2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352198"
---
# <a name="assembly-element-visual-studio-templates"></a>Элемент ASSEMBLY (шаблоны Visual Studio)
Указывает сведения о сборке, в шаблоне используется для добавления в проекты ссылки сборки.

 \<VSTemplate > \<TemplateContent > \<ссылки > \<ссылку > \<сборки >

## <a name="syntax"></a>Синтаксис

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Данный текст задает сборку, чтобы добавить в проект при создании экземпляра шаблона элемента. Имя сборки необходимо указать в одном из следующих способов:

- Как полное имя сборки. Пример:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Простой текст справки. Пример:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Примечания
 `Assembly` — обязательный дочерний элемент элемента `Reference`.

 `Reference`, `References,` И `Assembly` элементы могут использоваться только в *.vstemplate* файлы, имеющие `Type` значение атрибута `Item`.

## <a name="example"></a>Пример
 В следующем примере показано `TemplateContent` элемент шаблона элемента. Этот XML-код добавляет ссылки на *System.dll* и *System.Data.dll* сборок.

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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)