---
title: ВидимостьИзи Элемент Документы Майкрософт
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
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698191"
---
# <a name="visibilityconstraints-element"></a>Элемент VisibilityConstraints
Элемент VisibilityConstraints определяет статическую видимость групп команд и панелей инструментов. Видимость сначала контролируется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки (IDE) без загрузки VSPackage.

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
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент VisibilityItem](../extensibility/visibilityitem-element.md)|Определяет статическую видимость команд и панелей инструментов.|
|[ВидимостьИс](../extensibility/visibilityconstraints-element.md)|Определяет статическую видимость групп команд и панелей инструментов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды (например, пункты меню, меню, панели инструментов и комбо-коробки), которые VSPackage предоставляет IDE.|

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также
- [Элемент VisibilityItem](../extensibility/visibilityitem-element.md)
- [Командный стол Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
