---
title: Add stereotypes to UML model elements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292336"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Добавление стереотипов к элементам модели UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете добавить стереотип в элемент модели UML, чтобы указать для него заметку и предоставить ему специальные свойства. Чтобы добавить стереотип в элемент модели, стереотип должен быть определен в профиле, который следует связать с пакетом или моделью, содержащей соответствующий элемент модели. Каждый стереотип можно добавить только для определенных видов элементов модели, таких как классы, варианты использования или компоненты UML.

 Например, если вы хотите определить класс UML со стереотипом спецификации, необходимо создать его внутри пакета или модели, связанных со стандартным профилем L2.

 По умолчанию каждая модель связана со стандартными профилями L2 и L3 UML.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Связывание профиля с моделью или пакетом

1. Open **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Найдите пакет или модель, содержащие все элементы, к которым требуется применить стереотипы в профиле.

3. Right-click the package or the model and then click **Properties**.

4. In the **Properties** window, set the **Profiles** property to the profiles that contain the stereotypes you want to use.

     Стереотипы этого профиля станут доступны во всех элементах внутри модели или пакета. Если пакет содержит другие пакеты, стереотипы также будут доступны и в элементах внутри них.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Добавление стереотипов в элементы модели или отношения

1. Right-click the model element or relationship, either on a diagram or in **UML Model Explorer**, and then click **Properties**.

    > [!NOTE]
    > Чтобы добавить одни и те же стереотипы в несколько элементов, можно выбрать несколько элементов и щелкните один из них правой кнопкой мыши.

2. Click the **Stereotypes** property and select the stereotypes that you want to apply.

     для большинства видов элементов и отношений выбранные стереотипы заключаются в элементе модели в угловые скобки.

    > [!NOTE]
    > If you cannot see the **Stereotypes** property, or if the stereotype you want does not appear, verify that the model element is inside a package or a model to which the appropriate profile has been linked.

3. Некоторые стереотипы позволяют задавать значения дополнительных свойств для элемента модели. To see these properties, expand the **Stereotypes** property.

### <a name="to-create-model-elements-within-a-package"></a>Создание элементов модели внутри пакета

1. Create a package either in a UML Class Diagram, or in **UML Model Explorer**.

2. Добавьте элементы модели в пакет одним из следующих способов:

    - На UML-схеме классов щелкните инструмент для элемента, а затем щелкните внутри пакета на схеме.

         \- или -

    - In UML Model Explorer, right-click the package, point to **Add**, and then click an element type.

         \- или -

    - В обозревателе моделей UML перетащите существующий элемент в пакет.

         \- или -

    - Свяжите схему с пакетом, а затем создайте в ней элементы.

         To do this, right-click a blank part of the diagram and then click **Properties**. In the **Properties** window, set **Linked Package** to the package you want.

         Все создаваемые на схеме новые элементы будут определены внутри этого пакета.

         Это допускают только некоторые типы схем.

## <a name="see-also"></a>См. также раздел
 [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define packages and namespaces](../modeling/define-packages-and-namespaces.md)

