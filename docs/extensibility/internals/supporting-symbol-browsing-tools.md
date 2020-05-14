---
title: Поддержка инструментов символ-Браузера (ru) Документы Майкрософт
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704771"
---
# <a name="supporting-symbol-browsing-tools"></a>Вспомогательные средства просмотра символов
**Объект браузера**, **Просмотр класса**, **Call Browser** и Найти **символ Результаты** инструменты обеспечивают возможности просмотра символов в Visual Studio. Эти инструменты отображают иерархические виды деревьев символов и отображают отношения между символами на дереве. Символы могут представлять пространства имен, объекты, классы, членов классов и другие языковые элементы, содержащиеся в различных компонентах. Компоненты включают проекты Visual Studio, внешние компоненты .NET Framework и библиотеки типа (.tlb). Для получения дополнительной информации смотрите [О структуре кода](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Библиотеки символа-Брауинга
 Как деворенер языка, вы можете расширить возможности просмотра символов Visual Studio, создавая библиотеки, которые отслеживают символы в компонентах и предоставляют списки символов диспетчеру объектов Visual Studio через набор интерфейсов. Библиотека описывается интерфейсом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> Менеджер объектов Visual Studio отвечает на запросы о новых данных из инструментов просмотра символов, получая данные из библиотек и организуя их. Впоследствии он заполняет или обновляет инструменты с запрашиваемыми данными. Чтобы получить ссылку на менеджера <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>объекта Visual <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Studio, `GetService` передайте идентификатор службы методу.

 Каждая библиотека должна зарегистрироваться в центре внештатного объекта Visual Studio, который собирает информацию обо всех библиотеках. Чтобы зарегистрировать библиотеку, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> позвоните по методу. В зависимости от того, какой инструмент инициирует запрос, менеджер объектов Visual Studio находит соответствующую библиотеку и запрашивает данные. Данные перемещаются между [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] библиотеками и диспетчером <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> объектов в списках символов, описанных интерфейсом.

 Диспетчер [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] объектов отвечает за периодические обновления инструментов просмотра символов для отражения самых актуальных данных, содержащихся в библиотеках.

 Приведенная ниже диаграмма содержит выборку ключевых элементов процесса обмена запросами/данными между библиотекой и диспетчером объектов Visual Studio. Интерфейсы на диаграмме являются частью управляемого приложения кода.

 ![Поток данных между библиотекой и менеджером объекта](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Чтобы предоставить списки символов менеджеру объекта Visual Studio, необходимо сначала зарегистрировать библиотеку с менеджером объекта Visual Studio, позвонив по методу. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> После регистрации библиотеки диспетчер объектов Visual Studio запрашивает определенную информацию о возможностях библиотеки. Например, он запрашивает флаги библиотеки <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> и поддерживаемые категории, вызывая и методы. В какой-то момент, когда один из инструментов запрашивает данные из этой <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> библиотеки, диспетчер объектов запрашивает список символов верхнего уровня, вызывая метод. В ответ библиотека изготавливает список символов и предоставляет его <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> диспетчеру объектов Visual Studio через интерфейс. Диспетчер [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] объектов определяет, сколько элементов в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> списке, вызывая метод. Все следующие запросы относятся к данному элементу в списке и поставляют номер индекса товара в каждом запросе. Менеджер объектов Visual Studio начинает собирать информацию о типе, доступности и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> других свойствах элемента, вызывая метод.

 Он определяет имя элемента, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> метод и запрашивает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> информацию значка, вызывая метод. Значок отображается слева от имени элемента и изображает тип элемента, доступность и другие свойства.

 Диспетчер [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> вызывает метод, чтобы определить, является ли данный элемент списка расширяемым и содержит элементы детей. Если uI отправляет запрос на расширение элемента, диспетчер объекта запрашивает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> список символов, вызывая метод. Процесс продолжается с различными частями дерева строится по требованию.

> [!NOTE]
> Для реализации поставщика родного <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> используйте интерфейсы и интерфейсы.

## <a name="see-also"></a>См. также
- [Практическое руководство. Регистрация библиотеки с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Практическое руководство. Определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
