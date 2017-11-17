---
title: "Несколько доменного языка в одном решении | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="multiple-dsls-in-one-solution"></a>Несколько доменных языков в одном решении
Несколько доменных языков можно упаковать как часть единого решения, чтобы устанавливать их вместе.  
  
 Для интеграции нескольких доменных языков можно использовать различные технологии. Дополнительные сведения см. в разделе [интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) и [как: Добавление обработчика и перетащите](../modeling/how-to-add-a-drag-and-drop-handler.md) и [Настройка функции копирования](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Построение нескольких доменных языков в одном решении  
  
1.  Создайте два или несколько доменных языков и проект VSIX, а затем добавьте все проекты в одно решение.  
  
    -   Для создания нового проекта VSIX: В **новый проект** диалогового окна выберите **Visual C#**, **расширяемости**, **проект VSIX**.  
  
    -   Создайте одно или несколько решений доменного языка в каталоге решений VSIX.  
  
         Для каждого доменного языка откройте новый экземпляр в Visual Studio. Создайте новый доменный язык и укажите ту же папку решения, что и для решения VSIX.  
  
         Убедитесь, что каждый доменный язык создается с разным расширением имени файла.  
  
    -   Изменять имена **Dsl** и **DslPackage** проектов, чтобы все они отличаются. Примеры: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   В каждом **DslPackage\*\source.extension.tt**, обновить эту строку в правильное имя проекта Dsl:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   В решение VSIX, добавьте Dsl * и DslPackage\* проектов.  
  
         Можно добавить каждую пару в отдельную папку решения.  
  
2.  Объедините манифесты VSIX доменных языков:  
  
    1.  Откройте *YourVsixProject***\source.extension.manifest**.  
  
    2.  Для каждого DSL выберите **Добавление содержимого** и добавьте:  
  
        -   `Dsl*`проект в качестве **компонент MEF**  
  
        -   `DslPackage*`проект в качестве **компонент MEF**  
  
        -   `DslPackage*`проект в качестве **пакета VS**  
  
3.  Постройте решение.  
  
 Получившийся проект VSIX установит оба доменных языка. Можно проверить их, нажав клавишу F5 или развернуть *YourVsixProject***\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Способ: добавить обработчик перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Настройка функции копирования](../modeling/customizing-copy-behavior.md)