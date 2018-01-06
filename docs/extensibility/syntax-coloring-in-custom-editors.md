---
title: "Синтаксис, выделение цветом в редакторах | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8c40538b34c23e88b2c680db170b9d46b7b40f62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="syntax-coloring-in-custom-editors"></a>Синтаксис, выделение цветом в редакторах
Редакторы Visual Studio пакет SDK для среды, включая базового редактора, используйте службы языка для идентификации определенных синтаксических элементов и их отображения с цветами, заданного для представления данного документа.  
  
## <a name="colorization-requirements"></a>Выделение цветом требования  
 Все редакторы реализации colorizer языковую службу необходимо:  
  
1.  Используйте объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для управления текст, который будет цветом и объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> обеспечения представления текста документа.  
  
2.  Получите интерфейс для определенного языка службы с помощью запроса с помощью службы языков идентификатору GUID поставщика услуг в пакете VSPackage.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> объект, реализующий метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Этот метод связывает языковой службы с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> реализацию VSPackage, используемый для управления текст, который должен быть цветом.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Использование базового редактора языковую службу Colorizer  
 Когда языковую службу с colorizer получается путем экземпляр базового редактора, синтаксического анализа и обработки текста с помощью colorizer языковую службу происходит автоматически, не требуя дальнейшего вмешательства со стороны пользователя.  
  
 IDE прозрачно:  
  
-   Вызывает colorizer при необходимости для синтаксического анализа и анализа текста, как его при добавлении или изменении в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Гарантирует, что отображаемое, предоставляемые представления документов, предоставляемых <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> обновляется и окрашивание, используя информацию, возвращаемую colorizer реализации.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Использование редактора вспомогательные языковую службу Colorizer  
 Экземпляры базового отличный редактора можно также использовать языковую службу синтаксис Раскраска службы, но их необходимо явным образом получить и применить colorizer службы и перерисовать их представления документа, сами.  
  
 Для этого требуются вспомогательные редактор, чтобы:  
  
1.  Получить объект colorizer языковую службу (который реализует `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage делает это путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод интерфейса языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> метод для запроса, определенного фрагмента текста быть цветом.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Метод возвращает массив значений, один для каждого символа в тексте span выделение цветом. Он также определяет диапазон текста как определенный тип окрашиваемого объекта, например комментарий, ключевое слово или тип данных.  
  
3.  Выделение цветом сведения, возвращенные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> для перерисовки и отображения ее текста.  
  
> [!NOTE]
>  Помимо использования colorizer языковую службу, пакет VSPackage может быть использован универсального механизма выделения цветом текста пакет SDK для среды Visual Studio. Дополнительные сведения о механизме см. в разделе [использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>См. также  
 [Синтаксиса в языковую службу прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Реализация Цветовая подсветка синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)   
 [Как: использовать встроенные цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)