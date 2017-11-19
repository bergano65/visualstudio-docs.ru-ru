---
title: "Модель службы языка для прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afc15ea50921b1feca34a8b305c5028979a0d1ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="model-of-a-legacy-language-service"></a>Модель службы языка для прежних версий
Языковая служба определяет элементы и функции для конкретного языка и используются для предоставления редакторе сведения для данного языка. Например редактор необходимо знать элементов и ключевые слова языка, для поддержки Цветовая подсветка синтаксиса.  
  
 Языковая служба работает в тесном сотрудничестве с управляется редактора и представление, содержащее редактор буфер текста. Microsoft IntelliSense **краткие сведения** параметр приведен пример функции, предоставляемые языковой службы.  
  
## <a name="a-minimal-language-service"></a>Минимальный языковой службы  
 Самая базовая служба языка содержит два следующих объектов:  
  
-   *Языковая служба* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса. Языковая служба содержит сведения о языке, включая его имя, расширения имен файлов, диспетчер окон кода и colorizer.  
  
-   *Colorizer* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейса.  
  
 Ниже концептуальной показаны модели службы основного языка.  
  
 ![График языка модели службы](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Модель службы основного языка  
  
 Узлы окно документа *документов представление* редактора, в данном случае [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Представления документа текстового буфера владельцем редактора. Эти объекты работают с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] через окно документа специализированные вызов *окно кода*. Окно кода содержится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект, который создается и управляется в Интегрированной среде разработки.  
  
 При загрузке файла с расширением данного редактора находит языковой службы, связанной с этим расширением и передает ей окна кода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Служба возвращает язык *диспетчера окон кода*, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейса.  
  
 Ниже приводится обзор объектов в модели.  
  
|Компонент|Объект|Функция|  
|---------------|------------|--------------|  
|Буфер текста|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Чтение и запись текстового потока Юникода. Это возможно, что текст, который используется в других кодировках.|  
|Окно кода|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Окно документа, содержащего один или несколько представлений текста. Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в режиме многодокументного интерфейса (MDI), окно кода является дочерней формы MDI.|  
|Просмотр текста|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Окно, которое дает пользователю возможность перехода и просмотра текста с помощью клавиатуры и мыши. Текст отображается для пользователя как редактор. Можно использовать представления текста в обычный редактор windows, в окне вывода и окно "Интерпретация". Кроме того можно настроить одно или несколько представлений текст в окне кода.|  
|Диспетчер текста|Управляется <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службы, из которого можно получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> указатель|Компонент, который поддерживает общие сведения, совместно используется всеми компонентами, описанных выше.|  
|Служба языка|Реализация зависит от; реализует<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Объект, который предоставляет редактор зависящие от языка сведения, например подсветку синтаксиса, завершение операторов и проверка соответствия фигурных скобок.|  
  
## <a name="see-also"></a>См. также  
 [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)