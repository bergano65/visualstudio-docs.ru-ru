---
title: "Как: реализовать поиск и замена механизм | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c12e300a3537d1927710b0a4c3550ec3f5fd762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Как: реализовать поиск и замена механизм
Visual Studio предлагает два способа реализации поиска и замены. Можно передать текст изображение в оболочку и позвольте ему обрабатывать поиска, выделение и замена текста. Это позволяет пользователям указывать несколько фрагментов текста. Кроме того пакет VSPackage может управления этой функцией, сам. В обоих случаях необходимо уведомить оболочки о текущей цели и цели для всех открытых документов.  
  
### <a name="to-implement-findreplace"></a>Чтобы реализовать поиск и замена  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> интерфейс на одном из объектов, возвращенных свойства рамки <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> или <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. При создании пользовательского редактора, должны реализовывать этот интерфейс как часть класса настраиваемого редактора.  
  
2.  Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> метод, чтобы указать параметры, которые поддерживает редактора и для указания того, реализует ли текстовый поиск образа.  
  
     Если ваш редактор поддерживает текстовый поиск образа, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     В противном случае реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Если вы реализуете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> методы, можно упростить поиск задачи путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> интерфейса.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>