---
title: Несколько доменных языков в одном решении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668558"
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.

 Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в статьях [Интеграция моделей с помощью Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [инструкции: Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка поведения копирования](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Построение нескольких доменных языков в одном решении

1. Создайте два или несколько доменных языков и проект VSIX, а затем добавьте все проекты в одно решение.

   - Чтобы создать новый проект VSIX, в диалоговом окне " **Новый проект** " **выберите C#визуальный** элемент, **расширяемость**, **проект VSIX**.

   - Создайте одно или несколько решений доменного языка в каталоге решений VSIX.

        Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.

        Убедитесь, что каждый доменный язык создается с разным расширением имени файла.

   - Измените имена проектов **DSL** и **DslPackage** , чтобы они были разными. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - В каждом **DslPackage \* \ Source.extension.TT**измените эту строку на правильное имя проекта DSL:

        `string dslProjectName = "Dsl2";`

   - В решении VSIX добавьте проекты DSL * и DslPackage \*.

        Можно добавить каждую пару в отдельную папку решения.

2. Объедините манифесты VSIX доменных языков:

   1. Откройте _йоурвсикспрожект_ **\саурце.екстенсион.манифест**.

   2. Для каждого DSL выберите **Добавить содержимое** и добавьте:

       - `Dsl*` проект как **компонент MEF**

       - `DslPackage*` проект как **компонент MEF**

       - `DslPackage*` проект как **пакет VS**

3. Постройте решение.

   Получившийся проект VSIX установит оба доменных языка. Их можно проверить с помощью клавиши F5 или развернуть _йоурвсикспрожект_ **\bin\Debug \\ \*. VSIX**.

## <a name="see-also"></a>См. также раздел
 [Интеграция моделей с помощью Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [: Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md) [Настройка поведения копирования](../modeling/customizing-copy-behavior.md)
