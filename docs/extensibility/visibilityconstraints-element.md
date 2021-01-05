---
title: Элемент Висибилитиконстраинтс | Документация Майкрософт
description: Элемент Висибилитиконстраинтс определяет статическую видимость групп команд и панелей инструментов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f50f23847da8f6d56da6763146efd147aebca8c6
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863917"
---
# <a name="visibilityconstraints-element"></a>Висибилитиконстраинтс, элемент
Элемент Висибилитиконстраинтс определяет статическую видимость групп команд и панелей инструментов. Видимость сначала контролируется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки (IDE) без загрузки VSPackage.

## <a name="syntax"></a>Синтаксис

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Висибилититем, элемент](../extensibility/visibilityitem-element.md)|Определяет статическую видимость команд и панелей инструментов.|
|[висибилитиконстраинтс](../extensibility/visibilityconstraints-element.md)|Определяет статическую видимость групп команд и панелей инструментов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды (например, пункты меню, меню, панели инструментов и поля со списком), которые пакет VSPackage предоставляет интегрированной среде разработки.|

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также раздел
- [Висибилититем, элемент](../extensibility/visibilityitem-element.md)
- [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
