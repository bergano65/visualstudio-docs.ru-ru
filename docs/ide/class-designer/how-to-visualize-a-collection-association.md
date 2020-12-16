---
title: Визуализация ассоциации коллекции
description: Сведения о том, как визуализировать ассоциацию коллекции в конструкторе классов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaec7d97cd92e65671dedca14c2dbae056b1af10
ms.sourcegitcommit: 60e5a8a7ee91854356797d05f3b502572c4a4884
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933587"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Практическое руководство. Визуализация ассоциации коллекции в конструкторе классов

Свойства и поля, которые являются наборами других типов, могут отображаться в схеме классов как ассоциация набора. В отличие от обычной ассоциации, которая отображает поля или свойства в виде линии, связывающей класс-владелец с типом поля, ассоциация набора отображается как линия, связывающая класс-владелец с собранным типом.

## <a name="to-create-a-collection-association"></a>Создание ассоциации набора

1. В коде создайте свойство или поле, тип которого является строго типизированным набором.

2. В схеме классов разверните класс так, чтобы отображались свойства и поля.

3. В классе щелкните правой кнопкой мыши поле или свойство и выберите **Показывать как ассоциацию наборов**.

Свойство или поле отображается в виде линии ассоциации, связанной с собранным типом.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Создание ассоциаций между типами](how-to-create-associations-between-types.md)
- [Конструирование классов и типов](designing-and-viewing-classes-and-types.md)
