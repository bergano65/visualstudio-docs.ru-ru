---
title: "Вспомогательные средства просмотра символов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "символы, средства обзора символов"
  - "обозреватели, обозреватели символов"
  - "средства обзора символов"
  - "библиотеки"
  - "Интерфейс IVsLibrary2, средства обзора символов"
  - "Интерфейс IVsSimpleLibrary2, средства обзора символов"
  - "средства просмотра символов, диспетчер библиотек"
  - "символы"
  - "библиотеки, средства обзора символов"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Вспомогательные средства просмотра символов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**Обозреватель объектов**"  **Окно классов**"  **Обозреватель вызовов** и  **Результаты поиска символа** средства обеспечивают символ при просмотре возможности в Visual Studio.  Эти средства отображают иерархическое представление в виде дерева символов и отображают связи между символами в дереве.  Символы могут представлять пространства имен объектов, классы, члены класса и другие элементы языка, содержащихся в разных компонентах.  Компоненты включают проекты Visual Studio, внешние [!INCLUDE[.net framework]()] компоненты и библиотеки типов \(.tlb\).  Дополнительные сведения см. в разделе [Просмотр структуры кода](../../ide/viewing-the-structure-of-code.md).  
  
## Символ\-Просмотреть библиотеки  
 В реализации языка, можно расширить возможности Visual Studio символ\-просмотря путем создания библиотеки, которые отслеживают символы в компонентах и приводятся списки символов диспетчер объекта Visual Studio с помощью набора интерфейсов.  Библиотека описана  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> интерфейс.  Диспетчер объекта Visual Studio отвечает на запросы для новых данных с символ\-просмотря средств путем получения данных из библиотек и организации.  Он затем заполняет или обновлении средств с данными.  Получить ссылку на него объекта Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>передайте  <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> идентификатор службы  `GetService` метод.  
  
 Каждая библиотека должна зарегистрировать с помощью объекта Visual Studio, который собирает сведения обо всех библиотеках.  Чтобы зарегистрировать библиотеку, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.  В зависимости от того, программа инициирует запрос диспетчеру объекта Visual Studio найдет нужную библиотеку и запрашивает данные.  Данные передаются между библиотеками и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объекта в списках символов, описанных  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейс.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер периодически обновлять объекта отвечает за символ\-просмотрящ средства для текущие данные, которые содержатся в библиотеках.  
  
 Схема содержит образец ключевых положений ниже запросов\/процесса обмена данными между библиотекой и менеджером объектов Visual Studio.  Интерфейсы в схеме является частью приложения управляемого кода.  
  
 ![Поток данных между библиотекой и менеджером объекта](~/docs/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Для реализации списков символов диспетчер объекта Visual Studio, сначала необходимо зарегистрировать библиотеку с диспетчером объекта Visual Studio путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> метод.  После того как библиотека зарегистрирована диспетчер объекта Visual Studio запрашивает некоторое сведения о возможностях библиотеки.  Например, она запрашивает флаги библиотеки и поддерживаемые категории путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> методы.  Рано или поздно, когда средств запрашивать данные из этой библиотеки диспетчера объектов запрашивает список символов верхнего уровня, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> метод.  В ответе библиотека изготавливает список символов и представляет его на него объекта с помощью Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> интерфейс.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диспетчер объекта определяет, сколько элементов в списке путем вызова  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> метод.  Все приведенные ниже запросы, относящиеся к данному элементу в списке и предоставляют номер индекса элемента в каждом запросе.  Диспетчер объекта Visual Studio продолжает собирать сведения о типе специальных возможностях и других свойствах элемента, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> метод.  
  
 Он определяет имя элемента, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> метод и запросы данные значка путем вызова  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> метод.  Значок отображается слева от имени элемента и отображает тип элемента специальных возможностей и других свойств.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> диспетчер объекта вызывает  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] метод позволяет определить, является ли данный элемент списка расширяем и имеет дочерние элементы.  Если пользовательский интерфейс отправляет запрос развернуть элемент, то диспетчер объектов запрашивает список дочерних элементов символов, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> метод.  Процесс продолжается с разными частями дерева создаваемый по запросу.  
  
> [!NOTE]
>  Для реализации поставщика символов, используйте машинного кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> интерфейсы.  
  
## См. также  
 [Практическое руководство: зарегистрировать библиотеку с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Практическое руководство: предоставлять список символов, предоставленный библиотекой диспетчера объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Практическое руководство: определение символов в библиотеке](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)