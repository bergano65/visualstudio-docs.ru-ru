---
title: 'Как: реализовать поиск и замена механизм | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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