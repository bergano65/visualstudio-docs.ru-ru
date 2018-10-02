---
title: 'Практическое: реагирование на изменения в UML-модели | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: alancameronwills
ms.author: awills
manager: kamrani
ms.openlocfilehash: 07af0a9ee8fb31839343e853ee7175b204b7fe09
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558658"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Практическое руководство. Реагирование на изменения в UML-модели
Можно написать код, который будет выполняться при возникновении изменений в модели UML в Visual Studio. Такой код будет одинаково реагировать на изменения, внесенные самими пользователями, и на изменения, внесенные другими расширениями Visual Studio . Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!WARNING]
>  API UML эти методы не поддерживает. В будущих версиях Visual Studio они также могут не работать.  
  
 Пример кода доступен в [UML: Отклик на изменения в модели UML с помощью событий и правила](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)  
  
## <a name="see-also"></a>См. также  
 [Навигация по модели UML](../modeling/navigate-the-uml-model.md)   
 [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Пример: Цвет по стереотипу](http://go.microsoft.com/fwlink/?LinkId=213841)