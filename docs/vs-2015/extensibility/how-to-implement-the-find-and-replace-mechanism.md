---
title: Как реализовать механизм поиска и замены | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548701"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Практическое руководство. Реализация механизма поиска и замены
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio предоставляет два способа реализации поиска и замены. Один из способов — передать текстовое изображение в оболочку и позволить ему обрабатывать Поиск, выделение и замену текста. Это позволяет пользователям указывать несколько диапазонов текста. Кроме того, пакет VSPackage может управлять самой функцией. В обоих случаях необходимо уведомить оболочку о текущем целевом объекте и целевых объектах для всех открытых документов.  
  
### <a name="to-implement-findreplace"></a>Реализация поиска и замены  
  
1. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> интерфейс для одного из объектов, возвращаемых свойствами Frame <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> или <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . При создании пользовательского редактора следует реализовать этот интерфейс как часть класса пользовательского редактора.  
  
2. Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> метод, чтобы указать параметры, которые поддерживаются редактором, и указать, реализует ли он Поиск текстовых изображений.  
  
     Если редактор поддерживает поиск текстовых изображений, реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     В противном случае реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. При реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> методов и можно упростить выполнение задач поиска, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> интерфейс.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
