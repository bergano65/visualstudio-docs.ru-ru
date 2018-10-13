---
title: Цветовая маркировка синтаксиса в специализированных редакторах | Документация Майкрософт
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
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62fd407bdb377c490d26287701cf989a64484773
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305699"
---
# <a name="syntax-coloring-in-custom-editors"></a>Цветовая маркировка синтаксиса в специализированных редакторах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редакторы Visual Studio пакет SDK для среды, включая базовый редактор, использование служб языка, для идентификации определенных синтаксических элементов и их отображения с указанными цветами для представления данного документа.  
  
## <a name="colorization-requirements"></a>Требования к цветовое выделение  
 Все редакторы, реализация палитру языковой службы необходимо:  
  
1.  Использовать объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для управления текст, который необходимо выделить цветом и объект, реализующий интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для предоставления документа представления текста.  
  
2.  Получите интерфейс для определенной службы языка через запрос к поставщику службы в пакете VSPackage, с помощью службы языков идентификатору GUID.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> метод объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Этот метод связывает службы языка с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализацию VSPackage, используется для управления текст, который необходимо выделить цветом.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Использование палитру языковой службы базовым редактором  
 Когда службы языка с палитры получается путем экземпляр базового редактора, синтаксического анализа и визуализации текста с помощью палитры языковой службы происходит автоматически, не требуя какого-либо дальнейшего вмешательства со стороны пользователя.  
  
 Интегрированная среда разработки прозрачно:  
  
-   Вызывает палитры при необходимости для анализа и анализа текста, так как он добавляется или изменяется в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Гарантирует, что отображение, предоставляемые представления документов, предоставляемых <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> реализации обновляются и перерисована, используя сведения, возвращаемые функцией палитры.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Использование редактора неосновных палитру языковой службы  
 Экземпляры не базовый редактор можно также использовать службы цветовое выделение синтаксиса языковой службы, но их необходимо явным образом получить и применить службы палитры и перерисовать свои представления документа, сами.  
  
 Для этого требуется является редактором неосновных:  
  
1.  Получить объект палитру языковой службы (который реализует `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage делает это путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод в интерфейсе языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для запроса, что определенный диапазон текста, необходимо выделить цветом.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Метод возвращает массив значений, одной для каждой буквы в тексте span выделение цветом. Она также определяет диапазон текста, как определенный тип цветного элемента, например комментарий, ключевое слово или тип данных.  
  
3.  Использовать цветовое выделение сведения, возвращаемые функцией <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> для перерисовки и отображения текста.  
  
> [!NOTE]
>  Помимо использования палитры языковой службы, пакет VSPackage можно с использованием механизма общего назначения выделение цветом текста пакета SDK для среды Visual Studio. Дополнительные сведения о механизме, см. в разделе [использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>См. также  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация цветовой маркировки синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)   
 [Практическое: использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)

