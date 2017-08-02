---
title: "Предоставляет контекст языковой службы с помощью API прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Предоставляет контекст языковой службы с помощью API прежних версий
Существует два варианта языковую службу для предоставления контекста пользователя с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] базового редактора: предоставить текст маркера контекста или предоставить все контекста пользователя. Здесь описаны различия между ними.  
  
 Дополнительные сведения о предоставлении контекст языковой службы, который соединен с собственного редактора см. [как: предоставляют контекст для редакторов](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Предоставляет контекст маркера текст для редактора  
 Для предоставления контекста для ошибки компилятора, обозначенными текстовых меток в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основной редактор, следует реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>интерфейса.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> В этом случае служба языка предоставляет контекст только в том случае, когда курсор находится на текстовой метки. Это позволяет предоставляют ключевое слово в позиции курсора в редакторе **динамической справки** окно без атрибутов.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Предоставляет все контекст пользователя для редактора  
 Если вы создаете языковую службу и используете [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основной редактор, а затем можно реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>интерфейс для предоставления контекста для службы языка.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Для реализации `IVsLanguageContextProvider`, присоединяется к редактора, который отвечает за обновление контейнера контекста контейнер контекста (коллекция). Когда **динамической справки** окно вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>интерфейс на этот контейнер контекста в состоянии простоя, контекст контейнера запросы редактор для обновления.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> Редактор затем уведомляет языковую службу, ее следует обновить редактор и передает указатель на контекст контейнера. Это делается путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>метод из редактора для службы языка.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> С помощью указателя в контексте контейнера, языковая служба теперь добавлять и удалять атрибуты и ключевые слова. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>  
  
 Существует два различных способа реализации `IVsLanguageContextProvider`:  
  
-   Предоставляют ключевое слово в контексте контейнера  
  
     При вызове редактор для обновления контейнера контекста передайте соответствующие ключевые слова и атрибуты и возвращается `S_OK`. Это возвращаемое значение указывает, что редакторе, чтобы сохранить контекст ключевое слово и атрибут, а не предоставляет ключевого слова в позиции курсора в контексте контейнера.  
  
-   Получить ключевое слово из ключевого слова в позиции курсора  
  
     При вызове редактор для обновления контейнера контекста передать соответствующие атрибуты и возвращается `E_FAIL`. Это возвращаемое значение указывает, что редактор для сохранения атрибутов в контексте контейнера, но обновление контейнера контекста с помощью ключевого слова в позиции курсора.  
  
 На следующей схеме показана как контекст предоставляется для службы языка, который реализует `IVsLanguageContextProvider`.  
  
 ![График LangServiceImplementation2](~/docs/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
Контекст для службы языка  
  
 Как видно из диаграммы, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] основной текстовый редактор содержит контейнер контекста, присоединенные к нему. Этот контейнер контекст указывает три отдельных подконтекст сумки: языковой службы, редактора по умолчанию и текстовой метки. Языковой службы и текст маркера подконтекст контейнеры содержат атрибуты и ключевые слова для языковой службы, если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>реализации интерфейса и текстовых меток Если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>интерфейс реализован.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Если не реализовать один из этих интерфейсов, редактор предоставляет контекст для ключевого слова в позиции курсора в контейнере подконтекст редактора по умолчанию.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Правила контекста редакторы и конструкторы  
 Редакторы и конструкторы необходимо указать общее ключевое слово для окне редактора или конструктора. Это делается, чтобы отображает раздел справки универсальный, но возможно, для конструктора или редактора при нажатии клавиши F1. Редактор должен Помимо этого, задайте текущего ключевого слова в позиции курсора или предоставить основные термины, на основе текущего выделения. Это позволяет убедиться, что раздел справки для текста или элемент пользовательского интерфейса, на который указывает или выбран отображается при нажатии клавиши F1. Конструктор предоставляет контекст для элемента, выбранного в конструкторе, например кнопки на форме. Редакторы и конструкторы необходимо также подключаться к языковую службу как описано в разделе [Essentials службы языка прежних версий](../extensibility/internals/legacy-language-service-essentials.md).
