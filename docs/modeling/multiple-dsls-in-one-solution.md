---
title: "Несколько доменного языка в одном решении | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7b1ef7fc26cb0e46ecaf1853d6c9490016e68a5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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
  
    1.  Open *YourVsixProject***\source.extension.manifest**.  
  
    2.  Для каждого DSL выберите **Добавление содержимого** и добавьте:  
  
        -   `Dsl*`проект в качестве **компонент MEF**  
  
        -   `DslPackage*`проект в качестве **компонент MEF**  
  
        -   `DslPackage*`проект в качестве **пакета VS**  
  
3.  Постройте решение.  
  
 Получившийся проект VSIX установит оба доменных языка. Можно проверить их, нажав клавишу F5 или развернуть * YourVsixProject ***\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>См. также  
 [Интеграция моделей с помощью Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Способ: добавить обработчик перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Настройка функции копирования](../modeling/customizing-copy-behavior.md)