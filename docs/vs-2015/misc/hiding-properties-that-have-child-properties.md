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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822390"
---
# <a name="hiding-properties-that-have-child-properties"></a>Скрытие свойств, имеющих дочерние свойства
Необходимо скрыть свойства, имеющие дочерние свойства:  
  
- Если у вас есть вложенные проекты, в которых родительский проект программно управляет некоторыми аспектами дочернего проекта.  
  
- Если вы используете элемент управления с специализированным конструктором и не хотите предоставлять разработчикам полный доступ ко всем свойствам элемента управления.  
  
- Если вы владеете областью видимости объекта и хотите ограничить представление свойств.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Скрытие свойств, имеющих дочерние свойства  
  
1. Установите `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> значение `FALSE` .  
  
2. Установите `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> значение `TRUE` .  
  
## <a name="see-also"></a>См. также:  
 [Отображение сетки свойств](../extensibility/internals/properties-display-grid.md)