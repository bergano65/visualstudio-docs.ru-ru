---
title: Содержащиеся языки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184279"
---
# <a name="contained-languages"></a>Содержащиеся языки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*Содержащиеся языки* — это языки, которые содержатся на других языках. Например, HTML на [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] страницах могут содержать [!INCLUDE[csprcs](../includes/csprcs-md.md)] сценарии или [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Для редактора ASPX-файлов требуется архитектура с двумя языками, обеспечивающая IntelliSense, выделение цветом и другие функции редактирования как для HTML, так и для языка сценариев.  
  
## <a name="implementation"></a>Реализация  
 Самый важный интерфейс, который необходимо реализовать для автономных языков, — это <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Этот интерфейс реализуется любым языком, который может размещаться внутри основного языка. Он предоставляет доступ к цвету тонирования языковой службы, фильтру представления текста и ИДЕНТИФИКАТОРу службы основного языка. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Позволяет создать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Ниже показано, как реализовать содержащийся язык:  
  
1. Используйте `QueryService()` для получения идентификатора языковой службы и идентификатора интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> метод, чтобы создать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Передайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс, один или несколько [идентификаторов элементов](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейс.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>Интерфейс, который является объектом «координатор текстовых буферов», предоставляет базовые службы, необходимые для отображения расположений в первичном файле в буфере дополнительного языка.  
  
     Например, в одном ASPX-файле первичный файл включает в себя ASP, HTML и весь содержащийся в нем код. Однако вторичный буфер включает только содержащийся код вместе с любыми определениями классов, чтобы сделать вторичный буфер допустимым файлом кода. Координатор буферов обрабатывает работу по координации изменений из одного буфера в другой.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>Метод, который является основным языком, сообщает координатору буфера, какой текст в своем буфере сопоставлен с соответствующим текстом во вторичном буфере.  
  
     Язык передает массив <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> структуры, который в настоящее время включает только первичный и вторичный диапазон.  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>Метод и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> метод предоставляют сопоставление из первичного и вторичного буферов и наоборот.
