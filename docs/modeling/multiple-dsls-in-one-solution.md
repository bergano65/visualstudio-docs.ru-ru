---
title: Несколько доменных языков в одном решении
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c894ce7466c253916794495649fa65d703e6d67
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416153"
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении

Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.

Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в разделе [интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [как: Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка функции копирования](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Построение нескольких доменных ЯЗЫКОВ в одном решении

1. Создайте новый **проект VSIX** проекта.

2. Создайте два или несколько проектов DSL в каталоге решений VSIX.

   - Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.

   - Убедитесь, что каждый доменный язык создается с разным расширением имени файла.

   - Изменять имена **Dsl** и **DslPackage** проектов, чтобы они отличались. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - В каждом **DslPackage\*\source.extension.tt**, обновить эту строку на правильное имя проекта Dsl:

      `string dslProjectName = "Dsl2";`

   - В решение VSIX, добавьте Dsl * и DslPackage\* проектов. Можно добавить каждую пару в отдельную папку решения.

2. Объедините манифесты VSIX доменных языков:

   1.  Open _YourVsixProject_**\source.extension.manifest**.

   2.  Для каждого доменного языка выберите **добавить содержимое** и добавьте:

       -   `Dsl*` проект в качестве **компонент MEF**

       -   `DslPackage*` проект в качестве **компонент MEF**

       -   `DslPackage*` проект в качестве **пакета VS**

3. Постройте решение.

   Получившийся проект VSIX установит оба доменных языка. Можно протестировать с помощью клавиши F5 или развернуть _YourVsixProject_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>См. также

- [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Настройка функции копирования](../modeling/customizing-copy-behavior.md)