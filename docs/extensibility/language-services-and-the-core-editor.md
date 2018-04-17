---
title: Службы языка и базового редактора | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd9e0cdbcb10ac670ac1a0947fb9a43c16c7fccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="language-services-and-the-core-editor"></a>Службы языка и базового редактора
Редакторы в Visual Studio часто связаны с языковой службы. Помимо прочего языковая служба предоставляет Цветовая подсветка синтаксиса, завершение операторов, IntelliSense и форматирование текста.  
  
## <a name="core-editors-and-document-data-objects"></a>Редакторы ядра и объекты данных документа  
 При доступе к базового редактора, не следует создавать данные документа и объекты представления документа. Среда IDE создает и управляет этими двумя объектами, и получать дескрипторы их, выбрав соответствующие вызовы в редактора реализацию фабрики.  
  
 Дополнительные сведения см. в разделе [определение редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Службы языка и базового редактора  
 Путем реализации языковую службу, можно управлять отображением данных в представление документа. Языковая служба предоставляет информацию и поведение, характерное для данного языка, например Visual C++. Если создать текстовый буфер и определить расширение имени файла для открытия документа, буфер текста определяет языковой службы, связанный с расширением имени файла из раздела реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Editors \\\Extensions {YourLanguageService GUID}. Стандартная VSPackage, загрузка процедура затем загружает VSPackage и создать экземпляр службы языка.  
  
 На следующем рисунке показан базовый языковой службы.  
  
 ![График языка модели службы](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Базовые объекты службы редактора и язык  
  
 Объект данных документа для базового редактора называется буфер текста и представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объекта. Объект представления документа называется представлением текста и представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта. Эти два объекта совместно через службу языка для предоставления унифицированного представления базового редактора. Данные из буфера текста и отображает представление текста в окне документа вызывается окна кода. Окно документа кода управляется диспетчером окна кода.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Предоставляет контекст языковой службы с помощью API прежних версий](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Размещение IntelliSense](../extensibility/intellisense-hosting.md)   
 [Автономная языков](../extensibility/contained-languages.md)   
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)