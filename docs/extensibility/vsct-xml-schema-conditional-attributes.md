---
title: VsCT XML Схема Условные атрибуты (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697949"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы VSCT XML
Можно применить условные атрибуты ко всем спискам и элементам. Логические операторы и выражения расширения символов оценивают сяпотко или ложно. Если это так, связанный список или элемент включен в полученный вывод.

 Вы можете протестировать расширение токенов на другие расширения или константы токенов. Функция `Defined()` проверяет, было ли определено конкретное имя, даже если оно не имеет значения.

 При применении атрибута условия к списку условие применяется к каждому элементу ребенка в списке. Если элемент ребенка сам содержит атрибут состояния, то его состояние сочетается с выражением родительского элемента операцией AND.

 Значения 1, '1' и 'истинные' оцениваются как истинные, а 0, '0' и 'ложные' оцениваются как ложные.

## <a name="operators"></a>Операторы
 Используйте следующие операторы для оценки условных выражений.

|Оператор|Определение|
|--------------|----------------|
|(,)|Группирование|
|!|Логическое НЕ|
|\<, >, \<>,|Операторы отношения и равенства|
|и|Логическое|
|or|Логическое|

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

## <a name="see-also"></a>См. также
- [Командный стол Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
