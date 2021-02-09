---
title: Условные атрибуты схемы XML VSCT | Документация Майкрософт
description: Узнайте, как применять условные атрибуты для VSCT списков и элементов XML-схемы. Атрибуты оцениваются как true или false, контролируя результирующие выходные данные.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d123cfbd37c254522fe52bbb941afeb363d3fbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925753"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы XML VSCT
Условные атрибуты можно применять ко всем спискам и элементам. Логические операторы и выражения расширения символов имеют значение true или false. Если значение — true, связанный список или элемент включается в результирующие выходные данные.

 Расширения маркеров можно проверить по другим расширениям или константам. Функция `Defined()` проверяет, было ли определено определенное имя, даже если оно не имеет значения.

 При применении к списку атрибута Condition условие применяется к каждому дочернему элементу в списке. Если дочерний элемент содержит атрибут Condition, то его условие объединяется с родительским выражением операцией и.

 Значения 1, "1" и "true" оцениваются как true, а 0, "0" и "false" вычисляются как "false".

## <a name="operators"></a>Операторы
 Используйте следующие операторы для вычисления условных выражений.

|Оператор|Определение|
|--------------|----------------|
|(,)|Группирование|
|!|Логическое НЕ|
|\<, >, \<=, >=, ==, !=|Операторы отношения и равенства|
|и|Логическое|
|или диспетчер конфигурации служб|Логическое|

## <a name="examples"></a>Примеры

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>См. также раздел
- [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
