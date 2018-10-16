---
title: Скрытие свойств, имеющих дочерние свойства | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 76ef9c093bb91bc3cc22df7b56c4d5d69dbc41a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196525"
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