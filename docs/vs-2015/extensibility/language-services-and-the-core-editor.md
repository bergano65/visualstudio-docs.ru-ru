---
title: Языковые службы и базовый редактор | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180303"
---
# <a name="language-services-and-the-core-editor"></a>Языковые службы и основной редактор
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редакторы в среде Visual Studio часто связаны с языковой службой. Помимо прочего языковая служба предоставляет Цветовая подсветка синтаксиса, завершение операторов, IntelliSense и форматированием текста.  
  
## <a name="core-editors-and-document-data-objects"></a>Редакторы Core и объектов данных документа  
 При доступе к базовым редактором, не следует создавать данные документа и объекты представления документа. Среда IDE создает и управляет этими двумя объектами, и получить маркеры, чтобы их, выполнив соответствующие вызовы реализацию фабрики редактора.  
  
 Дополнительные сведения см. в разделе [определить, какой редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Языковые службы и основной редактор  
 Путем реализации языковой службы, можно управлять отображением данных в представление документа. Служба языка предоставляет информацию и поведение, характерное для данного языка, например Visual C++. При создании текстового буфера и определить расширение имени файла документа, который открывается, текстовый буфер определяет языковой службы, связанный с расширением имени файла из раздела реестра, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. Стандартный пакет VSPackage, загрузка процедура затем загружает VSPackage и создается экземпляр службы языка.  
  
 На следующем рисунке показан базовый языковой службы.  
  
 ![График языка модели службы](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Объекты ядра редактора и языковой службы  
  
 Объект данных документа для базового редактора называется текстового буфера, а также представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта. Объект представления документа называется представлением текста, а также представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта. Эти два объекта совместной работы через языковой службы для предоставления унифицированного представления базовым редактором. Сведения из текстового буфера и отображает представление текста в окне документа вызывается окна кода. Окно документа кода управляет диспетчер окон кода.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Предоставляет контекст службы языка с помощью API прежних версий](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Размещение IntelliSense](../extensibility/intellisense-hosting.md)   
 [Содержащихся языков](../extensibility/contained-languages.md)   
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)
