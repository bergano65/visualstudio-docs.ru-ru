---
title: Содержит языки | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7ec180689f4dadfb60832259ddee51a05f336fda
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="contained-languages"></a>Автономная языков

*Содержит языки* языки, которые находятся в других языках. Например, HTML в [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] страницы могут содержать [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] сценариев. Архитектура двумя языка требуется для редактора файл .aspx для предоставления IntelliSense, выделение цветом и другие возможности редактирования HTML и язык сценариев.

## <a name="implementation"></a>Реализация

Является наиболее важных интерфейса, необходимо реализовать для автономной языков <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейса. Этот интерфейс реализуется любой язык, который можно разместить внутри основного языка. Он предоставляет доступ к colorizer языковой службы, фильтр представления текста и ИД службы основного языка. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Позволяет создавать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейса. Ниже показано, как реализовать автономной языка:

1.  Используйте `QueryService()` для получения языка идентификатор службы и идентификатор интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Для создания <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс, вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> метод. Передайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса, один или несколько [элементов идентификаторы](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейса.

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Интерфейс, который является объект текстового буфера координатора, предоставляет основные службы, которые необходимы для сопоставления расположения в первичный файл в буфер дополнительный языки.

     Например в одном ASPX-файле, первичный файл включает ASP, HTML и весь код, который находится. Однако вторичный буфер содержит содержащийся внутри код вместе с определений классов для создания файла допустимый код вторичный буфер. Координатор буфера обрабатывающий координации изменений из одного буфера в другой.

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Метод, который является основным языком, сообщает координатора буфера текст внутри содержащего его буфера сопоставляется соответствующий текст в вторичный буфер.

     Язык передает массив <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> структуру, которая в настоящее время включает только основной и дополнительный диапазон.

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Метод и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> метод предоставляет сопоставление от основного на вторичный буфер и наоборот.