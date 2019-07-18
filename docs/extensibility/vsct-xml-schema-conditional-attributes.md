---
title: Условные атрибуты схемы VSCT XML | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11807129c34fa613ef06b3534adc7c7ebb9865e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322941"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы VSCT XML
Условные атрибуты можно применить ко всем списки и элементы. Логические операторы и выражения расширения символ оценки true или false. Значение true, если связанный список или элемент включается в результат.

 Вы можете протестировать маркеров расширения от других маркеров расширения или константы. Функция `Defined()` проверяет определенное имя будет определен, даже если он не имеет значения.

 При применении атрибута Condition в список условие применяется к каждый дочерний элемент в списке. Если сам дочерний элемент содержит атрибут Condition, затем его условие в сочетании с родительское выражение, оператор «и».

 Значения «true», "1" и 1 оцениваются как true, и 0, "0" и «false» получено значение false.

## <a name="operators"></a>Операторы
 Используйте следующие операторы для оценки условных выражений.

|Оператор|Определение|
|--------------|----------------|
|(,)|Группирование|
|!|Логическое НЕ|
|\<, >, \<=, >=, ==, !=|Операторы отношения и равенства|
|и|Boolean|
|или|Boolean|

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
- [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)