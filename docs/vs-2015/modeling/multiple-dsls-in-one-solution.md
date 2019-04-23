---
title: Несколько доменных языков в одном решении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d70794dddc02605c76c1af330a49af4be917c0e3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050144"
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.  
  
 Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в разделе [интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [как: Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка функции копирования](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Построение нескольких доменных языков в одном решении  
  
1. Создайте два или несколько доменных языков и проект VSIX, а затем добавьте все проекты в одно решение.  
  
   - Создание нового проекта VSIX В **новый проект** диалоговом окне выберите **Visual C#** , **расширяемости**, **проект VSIX**.  
  
   - Создайте одно или несколько решений доменного языка в каталоге решений VSIX.  
  
        Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.  
  
        Убедитесь, что каждый доменный язык создается с разным расширением имени файла.  
  
   - Изменять имена **Dsl** и **DslPackage** проектов, чтобы они отличались. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
   - В каждом **DslPackage\*\source.extension.tt**, обновить эту строку на правильное имя проекта Dsl:  
  
        `string dslProjectName = "Dsl2";`  
  
   - В решение VSIX, добавьте Dsl * и DslPackage\* проектов.  
  
        Можно добавить каждую пару в отдельную папку решения.  
  
2. Объедините манифесты VSIX доменных языков:  
  
   1. Open _YourVsixProject_**\source.extension.manifest**.  
  
   2. Для каждого доменного языка выберите **добавить содержимое** и добавьте:  
  
       - `Dsl*` проект в качестве **компонент MEF**  
  
       - `DslPackage*` проект в качестве **компонент MEF**  
  
       - `DslPackage*` проект в качестве **пакета VS**  
  
3. Постройте решение.  
  
   Получившийся проект VSIX установит оба доменных языка. Можно протестировать с помощью клавиши F5 или развернуть _YourVsixProject_**\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Практическое руководство. Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Настройка функции копирования](../modeling/customizing-copy-behavior.md)
