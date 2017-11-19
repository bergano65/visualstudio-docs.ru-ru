---
title: "Завершение операторов в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c694295c3456accc8d2c1cd3b0a1ec20f59343c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Завершение операторов в языковую службу прежних версий
Завершение операторов — это процесс, который помогает пользователям завершить ключевое слово языка или элемент, начатую ввод в редакторе основной языковой службы. Здесь описывается, как работает завершение операторов и как реализовать ее в службе языка.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Дополнительные сведения о новых способ реализации завершение операторов, в разделе [Пошаговое руководство: отображение завершение операторов](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementing-statement-completion"></a>Реализация завершение операторов  
 В редакторе core завершение операторов активирует специальный пользовательский Интерфейс, интерактивно поможет вам легко и быстро писать код. Завершение операторов помогает путем отображения соответствующих объектов или классов при необходимости, что позволяет избежать, необходимости запоминать конкретные элементы и без необходимости находить их в раздел ссылку справки.  
  
 Чтобы реализовать завершение операторов, язык должен иметь триггер завершение оператора, который может быть проанализирован. Например [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] использует оператор точки (.) при [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] использует стрелки (->) оператор. Чтобы инициировать завершение операторов языковую службу можно использовать более одного триггера. Эти триггеры программируются в фильтре команды.  
  
## <a name="command-filters-and-triggers"></a>Команда фильтры и триггеры  
 Команда фильтры перехватить вхождения триггер или триггеры. Чтобы добавить фильтр команды к представлению, реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса и присоединить ее к представлению, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Можно использовать один и тот же фильтр команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) для всех аспектов службы языка, например завершение операторов, маркеры ошибок и советы метод. Дополнительные сведения см. в разделе [перехват команды службы языка для прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 При вводе в редакторе триггера — в частности, буфер текста — вызывает службу языка <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод. В результате редактор открыть пользовательский Интерфейс, чтобы пользователь может выбирать кандидатов на завершение инструкции. Этот метод необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> и <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> флагов в качестве параметров. В списке элементов завершения отображается в списке с прокруткой. По мере ввода пользователем выделенного фрагмента в окне списка обновляется для отражения типизированные близкое последних символов. Базовый редактор реализует пользовательский Интерфейс для завершения операторов, но языковой службы необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс, чтобы определить набор кандидатов элементы завершения инструкции.  
  
## <a name="see-also"></a>См. также  
 [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)