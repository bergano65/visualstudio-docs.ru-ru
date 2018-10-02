---
title: Скрытие свойств, имеющих дочерние свойства | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569753"
---
# <a name="hiding-properties-that-have-child-properties"></a>Скрытие свойств, имеющих дочерние свойства
Требуется скрыть свойства, имеющих дочерние свойства:  
  
-   При наличии вложенных проектов, где родительский проект программным образом управляет некоторыми аспектами дочернему проекту.  
  
-   При использовании элемента управления с помощью специализированного конструктора, и вы не хотите предоставить разработчикам полный доступ ко всем свойствам элемента управления.  
  
-   Если у вас владения объектом в области действия и хотите ограничить представление свойств.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Чтобы скрыть свойства, имеющих дочерние свойства  
  
1.  Задайте `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> для `FALSE`.  
  
2.  Задайте `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> для `TRUE`.  
  
## <a name="see-also"></a>См. также  
 [Отображение сетки свойств](../extensibility/internals/properties-display-grid.md)