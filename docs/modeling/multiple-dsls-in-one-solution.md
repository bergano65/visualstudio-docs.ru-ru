---
title: Несколько доменных языков в одном решении
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f73fd8170c91fe51692c9ec5b5b39e7c36570dd2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949374"
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении
Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.

 Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в разделе [интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [как: Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка поведения копирования](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Построение нескольких доменных языков в одном решении

1. Создайте два или несколько доменных языков и проект VSIX, а затем добавьте все проекты в одно решение.

   -   Для создания нового проекта VSIX: В **новый проект** диалоговом окне выберите **Visual C#**, **расширяемости**, **проект VSIX**.

   -   Создайте одно или несколько решений доменного языка в каталоге решений VSIX.

        Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.

        Убедитесь, что каждый доменный язык создается с разным расширением имени файла.

   -   Изменять имена **Dsl** и **DslPackage** проектов, чтобы они отличались. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   -   В каждом **DslPackage\*\source.extension.tt**, обновить эту строку на правильное имя проекта Dsl:

        `string dslProjectName = "Dsl2";`

   -   В решение VSIX, добавьте Dsl * и DslPackage\* проектов.

        Можно добавить каждую пару в отдельную папку решения.

2. Объедините манифесты VSIX доменных языков:

   1.  Откройте _YourVsixProject_**\source.extension.manifest**.

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