---
title: Как реагировать на изменения в модели UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293398"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Практическое руководство. Реагирование на изменения в UML-модели
Можно написать код, который будет выполняться при возникновении изменений в модели UML в Visual Studio. Такой код будет одинаково реагировать на изменения, внесенные самими пользователями, и на изменения, внесенные другими расширениями Visual Studio . Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> API UML эти методы не поддерживает. В будущих версиях Visual Studio они также могут не работать.

## <a name="see-also"></a>См. также
 [Навигация по](../modeling/navigate-the-uml-model.md) [обработчикам событий модели UML изменение распространения изменений за пределами модели](../modeling/event-handlers-propagate-changes-outside-the-model.md) [— Выбор цвета по стереотипу](https://go.microsoft.com/fwlink/?LinkId=213841)