---
title: Элемент Groups | Документация Майкрософт
description: Элемент Groups содержит записи, определяющие группы команд VSPackage. Эта статья содержит пример.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b5885ad6e08bd9e22049033d6191c97fdc857b
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994294"
---
# <a name="groups-element"></a>Элемент Groups
Содержит записи, определяющие группы команд VSPackage.

## <a name="syntax"></a>Синтаксис

```xml
<Groups>
  <Group>... </Group>
  <Group>... </Group>
</Groups>
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
|[Group, элемент](../extensibility/group-element.md)|Представляет одну группу команд.|
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, определяющие группы команд VSPackage.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Commands, элемент](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов VSPackage.|

## <a name="example"></a>Пример

```xml
<Groups>
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
  </Group>
</Groups>
```

## <a name="see-also"></a>См. также раздел
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
