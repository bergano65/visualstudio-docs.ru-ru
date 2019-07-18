---
title: Пример расширения Excel. Класс ActionFilter | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c1dda46ed0e62649a576a12c9f9e48561ec891
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158161"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Пример расширения Excel. Класс ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот внутренний класс расширяет класс <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> и представляет фильтр для действий теста по отношению к элементу [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="simple-properties"></a>Простые свойства  
 Эти свойства только для чтения позволяют разработчику указывать, как фильтр действий теста должен применяться платформой закодированных тестов пользовательского интерфейса. Например, свойство <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> предоставляет имя фильтра действий. Другие свойства получают категорию (<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>) фильтра действий, тип фильтра (<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>), имя группы (<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>) для действий теста, фильтруемых данным фильтром действий. Другие свойства определяют, следует ли применять время ожидания (<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>), а также включен ли фильтр действий теста (<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>).  
  
## <a name="processrule-method"></a>Метод ProcessRule  
 Этот метод вызывается средой обработки закодированных тестов пользовательского интерфейса; он выполняет фильтр для предоставленного объекта <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>. Данное переопределение удаляет действие щелчка мыши в ячейке, если следующее действие в стеке отправляет нажатия клавиш клавиатуры в этой ячейке. Затем оно возвращает значение `false`.  
  
## <a name="private-methods"></a>Закрытые методы  
 Метод `IsLeftClick` определяет, представляет ли указанное действие щелчок левой кнопкой мыши. Метод `AreActionsOnSameExcelCell` определяет, выполняются ли два указанных действия в одной ячейке Excel.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
