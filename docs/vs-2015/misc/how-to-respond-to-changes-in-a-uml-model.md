---
title: 'Практическое: реагирование на изменения в UML-модели | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: kamrani
ms.openlocfilehash: 3dfb863828c20df36b59a66d7198613b1a21eb29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725212"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Практическое руководство. Реагирование на изменения в UML-модели
Можно написать код, который будет выполняться при возникновении изменений в модели UML в Visual Studio. Такой код будет одинаково реагировать на изменения, внесенные самими пользователями, и на изменения, внесенные другими расширениями Visual Studio . Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!WARNING]
>  API UML эти методы не поддерживает. В будущих версиях Visual Studio они также могут не работать.  
  
 Пример кода доступен в [UML: Отклик на изменения в модели UML с помощью событий и правила](http://code.msdn.microsoft.com/UML-Responding-to-changes-c024cd4b)  
  
## <a name="see-also"></a>См. также  
 [Навигация по модели UML](../modeling/navigate-the-uml-model.md)   
 [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Пример: Цвет по стереотипу](http://go.microsoft.com/fwlink/?LinkId=213841)