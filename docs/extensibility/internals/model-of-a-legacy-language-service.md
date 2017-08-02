---
title: "Модель службы языка прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы, модель"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Модель службы языка прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Служба языка определяет элементы и функции для определенного языка и используется для реализации редактора с конкретные сведения этот язык.  Например, редактор необходимо знать элементов и ключевые слова языка для поддержки расцветку синтаксиса.  
  
 Служба языка работает ближайшего с текстовый буфер, управляемый редактором и представлением, которое содержит редактор.  Microsoft IntelliSense **Краткие сведения** параметр пример функции, предоставленную службой языка.  
  
## Минимальная службы языка  
 Самая базовая служба языка содержит следующие 2 объекта:  
  
-   Служба языка реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс.  Служба языка содержит информацию о языке, включая его имя, расширения имени файла, диспетчер окон кода и colorizer.  
  
-   Colorizer реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.  
  
 Следующий документ концептуального показана модель базовой службы языка.  
  
 ![График языка модели службы](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Основная модель службы языка  
  
 Основные приложения окна документов представление документа в этом случае редактора [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] редактор.  Представление документа и текстовый буфер принадлежат редактором.  Эти объекты работают с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] специализированное с названием через окно документа a окно кода.  Окно кода содержится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект, созданный и управляется средой разработки.  
  
 Если файл с заданным расширением загрузке редактора находящий службу языка, связанная с этим расширением и передает ему окно кода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод.  Возвращает языковую службу a диспетчер окна кода, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.  
  
 В следующей таблице представлен обзор объектов модели.  
  
|Компонент|Объект.|Функция|  
|---------------|-------------|-------------|  
|Текстовый буфер|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Юникод чтения\/записи текстовый поток.  Текст может использовать другие кодировки.|  
|Окно кода|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Окно документа, которая содержит один или несколько представления текста.  После [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в режиме MDI \(MDI\) окно кода дочерний элемент MDI.|  
|Представление текста|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Окно, которое позволяет пользователю перемещаться и просматривать текст с помощью клавиатуры и мыши.  Представление текста отображается пользователю как редактор.  Можно использовать представления текста в обычных окнах редактора окне выходные данные и окне интерпретация.  Кроме того, можно настроить одну или несколько представлений текста в окне кода.|  
|Диспетчер текста|Управляемый код <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> служба, от которой вы получаете  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Указатель|Компонент, который поддерживает общие сведения совместно используемого всеми компонентами, описанными ранее.|  
|Служба языка|Зависимые реализации; реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Объект, который предоставляет редактор с данными о языковом как синтаксис при выборе, завершение выписки и проверка парности фигурных скобок.|  
  
## См. также  
 [Данные документа и представления документа в редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)