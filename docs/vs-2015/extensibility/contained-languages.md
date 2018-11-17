---
title: Содержащихся языков | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4ff50fe0fe156c548351c378ba3a256e230ec43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772030"
---
# <a name="contained-languages"></a>Содержащихся языков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

  
*Содержащихся языков* языков, которые содержатся в других языках. Например, HTML в [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] страницы могут содержать [!INCLUDE[csprcs](../includes/csprcs-md.md)] или [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] сценариев. Архитектура двумя языка является обязательным для редактора файла .aspx для обеспечения IntelliSense, выделение цветом и других функций редактирования HTML и язык сценариев.  
  
## <a name="implementation"></a>Реализация  
 Наиболее важным интерфейс необходимо реализовать для содержащихся языков <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Этот интерфейс реализуется в любом языке, могут размещаться в основной язык. Он предоставляет доступ к службе языка палитры, фильтр представления текста и идентификатор службы основного языка. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Позволяет создавать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Ниже показано, как реализовать содержащегося языка:  
  
1.  Используйте `QueryService()` для получения языка, код службы и идентификатор интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> метод для создания <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Передайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса, один или несколько [элементов идентификаторы](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейс.  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Интерфейс, который является объектом координатора буфера текста, предоставляет основные службы, которые необходимы для сопоставления расположения в первичный файл в буфер вторичного языка.  
  
     Например в одном ASPX-файле, первичный файл включает ASP, HTML и весь код, который содержится. Тем не менее вторичный буфер, включает в себя только содержащийся внутри код, вместе с определений классов для создания файла допустимый код вторичный буфер. Координатор буфера выполняет работу по координации изменений из одного буфера в другой.  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Метод, который является основным языком, сообщает координатор буфера текста внутри содержащего его буфера сопоставляется соответствующий текст во вторичном буфере.  
  
     Язык передает массив <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> структуру, которая в настоящее время включает только основной и дополнительный диапазон.  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Метод и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> метод предоставления сопоставление из первичного буфера во вторичный и наоборот.

