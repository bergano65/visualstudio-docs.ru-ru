---
title: "Языковые службы и базовый редактор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 13
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
ms.openlocfilehash: c78c3c5e450ffe348a8af2687e2b9b30b1128e8e
ms.lasthandoff: 02/22/2017

---
# <a name="language-services-and-the-core-editor"></a>Языковые службы и базовый редактор
Редакторы в Visual Studio часто связаны с языковой службы. Помимо прочего языковая служба предоставляет Цветовая подсветка синтаксиса, завершение операторов, IntelliSense и форматирование текста.  
  
## <a name="core-editors-and-document-data-objects"></a>Редакторы Core и объекты данных документа  
 При доступе к базового редактора, не следует создавать данных документов и объекты представления документа. Среда IDE создает и управляет этими двумя объектами, и получать дескрипторы их делая вызовы в редакторе реализацию фабрики.  
  
 Дополнительные сведения см. в разделе [определение редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Языковые службы и базовый редактор  
 Путем реализации службы языка, можно управлять отображением данных в представлении документов. Служба языка предоставляет информацию и поведение, характерное для данного языка, например Visual C++. При создании текстового буфера и определить расширение имени файла для открытия документа, в текстовом буфере определяет языковой службы, связанный с этим расширением имени файла из раздела реестра, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors\\\Extensions {YourLanguageService GUID}. Стандартная VSPackage, загрузка процедура затем загружает VSPackage и создается экземпляр службы языка.  
  
 На следующем рисунке показан службу языка basic.  
  
 ![График языка модели службы](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Базовые объекты службы редактора и языка  
  
 Объект данных документа для базового редактора называется текстового буфера и представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>объекта.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Объект представления документа называется представлением текста и представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>объекта.</xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Эти два объекта совместной работы через языковую службу для предоставления унифицированного представления базового редактора. Данные из текстового буфера и отображает представление текста в окне документа вызывается окна кода. Окно документа кода управляет диспетчер окон кода.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow></xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Предоставляет контекст языковой службы с помощью API прежних версий](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Размещение IntelliSense](../extensibility/intellisense-hosting.md)   
 [Автономные языков](../extensibility/contained-languages.md)   
 [Разработка языковую службу для прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)
