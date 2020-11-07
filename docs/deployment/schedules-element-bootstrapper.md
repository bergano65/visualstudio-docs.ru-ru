---
title: '&lt;Элемент Schedules &gt; (начальный загрузчик) | Документация Майкрософт'
description: Элемент Schedules содержит элементы расписания, которые определяют определенное время выполнения команд, определенных элементом Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f84727647f198c25175139412d3e8509e73fe1c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349364"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Элемент Schedules &gt; (начальный загрузчик)
`Schedules`Элемент содержит `Schedule` элементы, которые определяют определенное время выполнения команд, определенных `Command` элементом.

## <a name="syntax"></a>Синтаксис

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `Schedules`Элемент является дочерним по отношению к `Product` элементу. Каждый `Product` элемент может иметь не более одного `Schedules` элемента. У элемента `Schedules` нет атрибутов.

## <a name="schedule"></a>Расписание
 `Schedule`Элемент является дочерним по отношению к `Schedules` элементу. `Schedules`Элемент должен иметь по крайней мере один `Schedule` элемент.

 `Schedule` имеет следующий атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный элемент. Имя элемента расписания. Это соответствует `ScheduleName` свойству `Command` элемента. Когда объект `Command` ссылается на именованное расписание, он будет выполняться только в момент, указанный этим `Schedule` элементом. Расписания также могут быть связаны с `FailIf` элементами и `BypassIf` , которые ограничивают эти условные тесты для выполнения по указанному расписанию. Дополнительные сведения см. в разделе [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|

 Данный `Schedule` элемент может иметь только один из следующих дочерних элементов.

## <a name="buildlist"></a>буилдлист
 `BuildList`Элемент указывает установщику выполнить команду сразу после запуска приложения начальной загрузки.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`Элемент указывает установщику выполнить команду перед установкой указанного пакета.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`Элемент указывает установщику выполнить команду после установки указанного пакета.

## <a name="see-also"></a>См. также
- [\<Product> дерев](../deployment/product-element-bootstrapper.md)
- [Справочник по схеме продуктов и пакетов](../deployment/product-and-package-schema-reference.md)