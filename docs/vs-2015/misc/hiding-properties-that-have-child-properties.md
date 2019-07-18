---
title: Скрытие свойств, имеющих дочерние свойства | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822390"
---
# <a name="hiding-properties-that-have-child-properties"></a>Скрытие свойств, имеющих дочерние свойства
Требуется скрыть свойства, имеющих дочерние свойства:  
  
- При наличии вложенных проектов, где родительский проект программным образом управляет некоторыми аспектами дочернему проекту.  
  
- При использовании элемента управления с помощью специализированного конструктора, и вы не хотите предоставить разработчикам полный доступ ко всем свойствам элемента управления.  
  
- Если у вас владения объектом в области действия и хотите ограничить представление свойств.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Чтобы скрыть свойства, имеющих дочерние свойства  
  
1. Задайте `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> для `FALSE`.  
  
2. Задайте `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> для `TRUE`.  
  
## <a name="see-also"></a>См. также  
 [Отображение сетки свойств](../extensibility/internals/properties-display-grid.md)