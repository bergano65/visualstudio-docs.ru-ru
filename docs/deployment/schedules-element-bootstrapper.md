---
title: '&lt;Расписания&gt; элемент (загрузчик) | Документация Майкрософт'
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
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639431"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Расписания&gt; элемент (установщик)
`Schedules` Элемент содержит `Schedule` элементы, которые определяют времена команд, определенных по `Command` элемент должен выполняться.

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
 `Schedules` Элемент является дочерним элементом `Product` элемент. Каждый `Product` элемент может содержать не более одного `Schedules` элемент. У элемента `Schedules` нет атрибутов.

## <a name="schedule"></a>Расписание
 `Schedule` Элемент является дочерним элементом `Schedules` элемент. Объект `Schedules` элемент должен иметь по крайней мере `Schedule` элемент.

 `Schedule` содержит следующий атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный. Имя элемента расписания. Это соответствует `ScheduleName` свойство `Command` элемент. Когда `Command` ссылается на именованное расписание будет выполняться только по этим в указанное время `Schedule` элемент. Расписания также могут быть связаны с `FailIf` и `BypassIf` элементы, которые ограничивают эти условия выполнения по указанному расписанию. Дополнительные сведения см. в разделе [ \<команды > элемент](../deployment/commands-element-bootstrapper.md).|

 Заданный `Schedule` элемент может иметь только один из следующих дочерних элементов.

## <a name="buildlist"></a>BuildList
 `BuildList` Элемент указывает, что установщик, чтобы выполнить команду, сразу после запуска приложение начальной загрузки.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage` Элемент указывает, что установщик, чтобы выполнить команду перед установкой указанного пакета.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage` Элемент указывает, что установщик, чтобы выполнить команду после установки указанного пакета.

## <a name="see-also"></a>См. также
- [\<Продукт > элемент](../deployment/product-element-bootstrapper.md)
- [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)