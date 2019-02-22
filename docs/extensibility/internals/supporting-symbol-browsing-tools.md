---
title: Вспомогательные средства просмотра символов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d3d15f6d38ab494c586f22cc428d5e00442e84
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617006"
---
# <a name="supporting-symbol-browsing-tools"></a>Вспомогательные средства просмотра символов
**Обозреватель объектов**, **представление классов**, **Обозреватель вызовов** и **результаты поиска символа** средства предоставляют средства в Visual Studio для просмотра символов. Эти средства просмотра представлений иерархическом дереве символов и отображения связей между символы в дереве. Символы могут представлять пространства имен, объекты, классы, члены класса и остальных элементов языка, содержащиеся в различных компонентов. Компоненты включают проекты Visual Studio, внешних [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] компоненты и библиотеки типов (TLB). Дополнительные сведения см. в разделе [Просмотр структуры кода](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Библиотеки просмотра символов
 Как язык исполнителя можно расширить возможности просмотра символов Visual Studio путем создания библиотек, отслеживать символы в компонентах и предоставляют списки по принципу символов в диспетчер объектов Visual Studio через набор интерфейсов. Описывается библиотека <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> интерфейс. Диспетчер объектов Visual Studio отвечает на запросы для новых данных с помощью средств просмотра символов, получение данных из библиотеки и организуя их. Затем заполняет или обновляет средства запрошенные данные. Для получения ссылки на диспетчер объектов Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, передайте <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор для службы `GetService` метод.

 Каждая библиотека необходимо зарегистрировать с диспетчером объектов Visual Studio, который собирает сведения о всех библиотек. Чтобы зарегистрировать библиотеку, вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. В зависимости от того, какое средство инициирует запрос диспетчер объектов Visual Studio находит соответствующую библиотеку и запрашивает данные. Эти данные передаются между библиотеками и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчера объектов в списках символов, описываемого <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейс.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Диспетчера объектов отвечает за периодическом ее обновлении средства просмотра символов, с учетом самых последних данных, содержащихся в библиотеках.

 На схеме ниже приведен пример ключевые элементы процесса exchange запросов и данных между библиотекой и менеджером объекта Visual Studio. На схеме интерфейсов являются частью приложения управляемого кода.

 ![Поток данных между библиотекой и менеджером объекта](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Чтобы предоставить список символов диспетчера объектов Visual Studio, необходимо сначала зарегистрировать библиотеку с диспетчером объектов Visual Studio путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод. После регистрации библиотеки диспетчера объектов Visual Studio запрашивает определенные сведения о возможностях библиотеки. Например, он запрашивает флаги библиотеки и поддерживается категорий путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> методы. В будущем, если один из инструментов запрашивает данные из этой библиотеки диспетчера объектов запрашивает верхнего уровня список символов путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> метод. В ответ, библиотека создает список символов и делает его уязвимым для диспетчера объектов Visual Studio через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейс. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Диспетчера объектов определяет, сколько элементов находятся в списке, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> метод. Все следующие запросы, относящиеся к данному элементу в списке и укажите номер индекса элемента в каждом запросе. Диспетчер объектов Visual Studio продолжает собирать информацию на тип, доступность и другие свойства элемента путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> метод.

 Он определяет имя элемента, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> метод и запрашивает сведения о ярлыка путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> метод. Значок отображается слева от имени элемента и описывается тип элемента, доступность и другие свойства.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Manager вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> метод, чтобы определить, если указанный элемент списка является расширяемым и содержит дочерние элементы. Если пользовательский Интерфейс отправляет запрос, чтобы развернуть элемент, диспетчер объектов запрашивает дочерний список символов путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> метод. Процесс продолжается с разными частями дерева, создаваемую по запросу.

> [!NOTE]
>  Для реализации поставщика символов машинного кода, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> интерфейсов.

## <a name="see-also"></a>См. также
- [Практическое руководство. Зарегистрировать библиотеку с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Практическое руководство. Раскрывать списки символов, предоставляемые библиотекой в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Практическое руководство. Определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)