---
title: Языковые службы и основной редактор | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180303"
---
# <a name="language-services-and-the-core-editor"></a>Языковые службы и основной редактор
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редакторы в Visual Studio часто связаны с языковой службой. Помимо прочего, языковая служба обеспечивает выделение синтаксиса, завершение операторов, IntelliSense и форматирование текста.  
  
## <a name="core-editors-and-document-data-objects"></a>Базовые редакторы и объекты данных документов  
 При доступе к основному редактору не создаются объекты данных и представления документов. Интегрированная среда разработки создает и управляет этими двумя объектами и получает дескрипторы для них, выполнив соответствующие вызовы в реализации фабрики редактора.  
  
 Дополнительные сведения см. [в разделе Определение редактора, открывающего файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Языковые службы и основной редактор  
 Реализуя языковую службу, можно управлять отображением данных в представлении документа. Языковая служба предоставляет сведения и поведение, характерное для конкретного языка, например Visual C++. При создании текстового буфера и определении расширения имени файла для открываемого документа текстовый буфер определяет языковую службу, связанную с этим расширением имени файла, из раздела реестра HKEY_LOCAL_MACHINE \Софтваре\микрософт\едиторс \\ {ЙОУРЛАНГУАЖЕСЕРВИЦЕ GUID} \екстенсионс. Затем стандартная процедура загрузки VSPackage загружает пакет VSPackage и создается экземпляр языковой службы.  
  
 На следующем рисунке показана основная языковая служба.  
  
 ![График языка модели службы](../extensibility/media/vslanguageservicemodel.gif "вслангуажесервицемодел")  
Основные объекты редактора и языковой службы  
  
 Объект данных документа для базового редактора называется текстовым буфером и представлен <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объектом. Объект представления документа называется текстовым представлением и представляется <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объектом. Эти два объекта работают совместно через языковую службу, чтобы обеспечить единое представление основного редактора. Сведения из текстового буфера и текстового представления отображаются в окне документа, называемом окном кода. Документ в окне кода управляется диспетчером окна кода.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Предоставление контекста языковой службы с помощью API прежних версий](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Размещение IntelliSense](../extensibility/intellisense-hosting.md)   
 [Автономные языки](../extensibility/contained-languages.md)   
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)
