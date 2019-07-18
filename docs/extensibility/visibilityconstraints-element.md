---
title: Элемент VisibilityConstraints | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee64b4b8ccebe6e63b5c558df68e0a5625b37884
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310668"
---
# <a name="visibilityconstraints-element"></a>Элемент VisibilityConstraints
Элемент VisibilityConstraints определяет видимость статических групп, команд и панелей инструментов. Видимость сначала управляется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) без загрузки VSPackage.

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
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент VisibilityItem](../extensibility/visibilityitem-element.md)|Определяет статические видимость команды и панели инструментов.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Определяет видимость статических групп, команд и панелей инструментов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды (например, элементы меню, меню, панелей инструментов и поля со списком), которые VSPackage предоставляет интегрированную среду разработки.|

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также
- [Элемент VisibilityItem](../extensibility/visibilityitem-element.md)
- [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
