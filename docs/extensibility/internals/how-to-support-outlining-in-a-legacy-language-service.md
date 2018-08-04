---
title: 'Практическое: поддержка структурирования в языковой службе прежних версий | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6f9ba947aee0276e2cca6270438cdaf20e7626e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510961"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Практическое: поддержка структурирования в языковой службы прежних версий
Структурирование позволяет развернуть или свернуть другой области текста. Способ структурирования используется можно определить по-разному в разных языках. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать структурирование, см. в разделе [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Ниже показано, как для поддержки этой команды для языковой службы.  
  
## <a name="to-support-outlining"></a>Для поддержки структурирование  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объект языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> на текущий объект сеанса структуры для добавления новых структурные области.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Когда пользователь выбирает **свернуть в определения** на **структура** меню, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> в службе языка.  
  
 При вызове этот метод передает интегрированной среды разработки <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель (указатель на текстовый буфер) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (указатель в текущий сеанс структуры).  
  
 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей структуры, указав этих регионов в `rgOutlnReg` параметра. `rgOutlnReg` Параметр <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структуры. Этот процесс позволяет указывать разные характеристики скрытой области, такие как развернут или свернут определенного региона.  
  
> [!NOTE]
>  Следите за тем, о скрытии символы новой строки. Скрытый текст должен следовать от начала первой строки до последней символ последней строки в разделе, оставляя видимым последним символом новой строки.  
  
## <a name="see-also"></a>См. также  
 [Практическое: укажите скрытого текста поддержки в языковой службы прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Практическое: Расширенная поддержка структурирования в языковой службы прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)