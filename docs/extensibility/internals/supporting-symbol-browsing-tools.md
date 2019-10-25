---
title: Поддержка средств обзора символов | Документация Майкрософт
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723084"
---
# <a name="supporting-symbol-browsing-tools"></a>Вспомогательные средства просмотра символов
**Обозреватель объектов**, **представление классов**, **Обозреватель вызовов** и **Поиск результатов поиска символов** предоставляют возможности просмотра символов в Visual Studio. Эти средства отображают иерархические древовидные представления символов и отображают связи между символами в дереве. Символы могут представлять пространства имен, объекты, классы, члены классов и другие элементы языка, содержащиеся в различных компонентах. Компоненты включают в себя проекты Visual Studio, внешние .NET Framework компонентов и типов (TLB) библиотеки. Дополнительные сведения см. в разделе [Просмотр структуры кода](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Библиотеки обзора символов
 Как разработчик языка можно расширять возможности просмотра символов в Visual Studio, создавая библиотеки, которые отписывают символы в компонентах и предоставляют списки символов для диспетчера объектов Visual Studio с помощью набора интерфейсов. Библиотека описывается интерфейсом <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>. Диспетчер объектов Visual Studio реагирует на запросы новых данных из средств обзора символов, получая данные из библиотек и упорядочивая их. Впоследствии он заполняет или обновляет средства с помощью запрошенных данных. Чтобы получить ссылку на диспетчер объектов Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, передайте идентификатор службы <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> в метод `GetService`.

 Каждая библиотека должна быть зарегистрирована в диспетчере объектов Visual Studio, которая собирает сведения обо всех библиотеках. Чтобы зарегистрировать библиотеку, вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. В зависимости от того, какой инструмент инициирует запрос, диспетчер объектов Visual Studio находит соответствующую библиотеку и запрашивает данные. Данные передаются между библиотеками и диспетчером объектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в списках символов, описываемых интерфейсом <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>.

 Диспетчер объектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отвечает за периодическое обновление средств обзора символов для отражения самых актуальных данных, содержащихся в библиотеках.

 На приведенной ниже схеме показан пример ключевых элементов процесса обмена запросами и данными между библиотекой и диспетчером объектов Visual Studio. Интерфейсы на схеме являются частью приложения с управляемым кодом.

 ![Поток данных между библиотекой и диспетчером объектов](../../extensibility/internals/media/callbrowserdiagram.gif "каллбровсердиаграм")

 Чтобы предоставить список символов для диспетчера объектов Visual Studio, необходимо сначала зарегистрировать библиотеку с помощью диспетчера объектов Visual Studio, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. После регистрации библиотеки диспетчер объектов Visual Studio запрашивает определенные сведения о возможностях библиотеки. Например, он запрашивает флаги библиотеки и поддерживаемые категории, вызывая методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>. В некоторый момент, когда один из средств запрашивает данные из этой библиотеки, диспетчер объектов запрашивает список символов верхнего уровня, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>. В ответ библиотека создает список символов и предоставляет их диспетчеру объектов Visual Studio через интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>. Диспетчер объектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] определяет количество элементов в списке, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>. Все следующие запросы относятся к заданному элементу в списке и указывают номер индекса элемента в каждом запросе. Диспетчер объектов Visual Studio продолжает получать сведения о типе, доступе и других свойствах элемента, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>.

 Он определяет имя элемента, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> и запрашивает сведения о значке, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>. Значок отображается слева от имени элемента и показывает тип элемента, доступность и другие свойства.

 Диспетчер объектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>, чтобы определить, является ли заданный элемент списка расширяемым и наличием дочерних элементов. Если пользовательский интерфейс отправляет запрос на расширение элемента, диспетчер объектов запрашивает дочерний список символов, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>. Процесс продолжится с различными частями дерева, построенными по запросу.

> [!NOTE]
> Для реализации собственного поставщика символов кода используйте интерфейсы <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>.

## <a name="see-also"></a>См. также
- [Практическое руководство. Регистрация библиотеки с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Практическое руководство. Определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)