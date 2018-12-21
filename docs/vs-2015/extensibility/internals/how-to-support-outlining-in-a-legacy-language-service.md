---
title: 'Практическое: поддержка структурирования в языковой службе прежних версий | Документация Майкрософт'
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
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb596c8fbc7ab3c354b5b8d3e2a116ee752f06a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724130"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Практическое: поддержка структурирования в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Структурирование позволяет развернуть или свернуть другой области текста. Способ структурирования используется можно определить по-разному в разных языках. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать структурирование, см. в разделе [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Ниже показано, как для поддержки этой команды для языковой службы.  
  
### <a name="to-support-outlining"></a>Для поддержки структурирование  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объект языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> на текущий объект сеанса структуры для добавления новых структурные области.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Когда пользователь выбирает **свернуть в определения** на **структура** меню, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> в службе языка.  
  
 При вызове этот метод передает интегрированной среды разработки <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель (указатель на текстовый буфер) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (указатель в текущий сеанс структуры).  
  
 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей структуры, указав этих регионов в `rgOutlnReg` параметра. `rgOutlnReg` Параметр <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структуры. Этот процесс позволяет указать разные характеристики скрытой области, такие как развернут или свернут определенного региона.  
  
> [!NOTE]
>  Следите за тем, о скрытии символы новой строки. Скрытый текст должен следовать от начала первой строки до последней символ последней строки в разделе, оставляя видимым последним символом новой строки.  
  
## <a name="see-also"></a>См. также  
 [Практическое: поддержка скрытого текста в языковой службе прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

