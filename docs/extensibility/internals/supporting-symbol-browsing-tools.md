---
title: "Поддержка средства обзора символ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78a4e910dbd2c6063f4bdf7b0dff3f27f79b218e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-symbol-browsing-tools"></a>Вспомогательные средства обзора символ
**Обозреватель объектов**, **представление классов**, **обозревателя вызовов** и **результаты поиска символа** средства предоставляют средства в Visual Studio для просмотра символов. Эти средства отображают иерархическое дерево представления символов и отображения связей между символами в дереве. Символы могут представлять пространства имен, объекты, классы, члены класса и остальные элементы языка, содержатся в различных компонентов. Компоненты включают внешних проектов Visual Studio [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] компоненты и библиотеки типов (TLB). Дополнительные сведения см. в разделе [Просмотр структуры кода](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Просмотр символов библиотеки  
 Как исполнителя языка просматриваемого символа возможности Visual Studio можно расширить путем создания библиотеки, которые отслеживают символы в компонентах и предоставляют списки символов в диспетчер объектов Visual Studio через набор интерфейсов. Описывается библиотека <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> интерфейса. Диспетчер объектов Visual Studio отвечает на запросы для новых данных из средств просмотра символов для получения данных из библиотек, организуя их. Затем заполняет или обновляет средства запрошенные данные. Для получения ссылки на диспетчер объектов Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор для службы `GetService` метод.  
  
 Каждая библиотека необходимо зарегистрировать в диспетчере объектов Visual Studio, который собирает сведения о всех библиотек. Чтобы зарегистрировать библиотеку, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. В зависимости от того, какой инструмент инициирует запрос диспетчер объектов Visual Studio находит соответствующую библиотеку и запрашивает данные. Эти данные передаются между библиотеками и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов в списках символов, описываемого <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейса.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Диспетчер объектов отвечает за периодически обновление средства обзора символ для отражения последних данных, содержащихся в библиотеках.  
  
 Ниже приведен пример основными элементами процесса обмена запросов и данных между библиотекой и менеджером объекта Visual Studio. На схеме интерфейсов являются частью приложения с управляемым кодом.  
  
 ![Поток данных между библиотекой и менеджером объекта](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Чтобы предоставить списки символы диспетчер объектов Visual Studio, необходимо сначала зарегистрировать библиотеку с помощью диспетчера объектов Visual Studio путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. После регистрации библиотеки диспетчера объектов Visual Studio запрашивает определенные сведения о возможностях библиотеки. Например, запрашивает флаги библиотеки и поддерживается категорий путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> методы. В определенный момент при одного из средств запрашивает данные из этой библиотеки диспетчера объектов запрашивает список символов верхнего уровня, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> метод. В ответ, библиотеке изготавливает список символов и делает его уязвимым для диспетчера объектов Visual Studio через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Диспетчера объектов определяет, сколько элементов в списке, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> метод. Все следующие запросы относится к заданному элементу в списке и введите номер индекса элемента в каждом запросе. Диспетчер объектов Visual Studio продолжает собирать данные в тип, доступность и другие свойства элемента путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> метод.  
  
 Он определяет имя элемента, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> метод и запрашивает сведения значок путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> метод. Значок отображается слева от имени элемента и показывает тип элемента, доступность и другие свойства.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Диспетчер вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> метод для определения, если элемент списка является расширяемым и имеет дочерних элементов. При отправке запроса разверните элемент пользовательского интерфейса диспетчера объектов запрашивает список дочерних символов посредством вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> метод. Процесс продолжается с использованием различных частей дерева создающимся по требованию.  
  
> [!NOTE]
>  Для реализации поставщика символ машинного кода, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> интерфейсов.  
  
## <a name="see-also"></a>См. также  
 [Как: регистрации библиотеки с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Как: предоставлять список символов, предоставленный библиотекой диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Практическое руководство. Определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)