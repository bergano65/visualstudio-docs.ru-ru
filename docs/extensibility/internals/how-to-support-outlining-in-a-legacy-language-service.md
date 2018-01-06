---
title: "Как: поддерживает структуризация в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa57b0d09cb8422a9dde1f70306d2f3808b0384e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Как: поддерживает структуризация в языковую службу прежних версий
Структурирование позволяет развернуть или свернуть различных областей текста. Используется как структурирование определены по-разному в разных языках. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Чтобы больше узнать о том, как реализовать структурирование новый, в разделе [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
 Следующий пример демонстрирует для поддержки этой команды для службы языка.  
  
### <a name="to-support-outlining"></a>Для поддержки структурирование  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объект языковой службы.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> с текущим объектом сеанса структурирования, чтобы добавить новый структурные области.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Когда пользователь выбирает **свертывания в определения** на **структура** меню, вызовы IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> в службе языка.  
  
 При вызове этот метод передает IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> указатель (указатель на буфер текста) и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (указатель на текущий сеанс структурирования).  
  
 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей структуры путем указания этих областей в `rgOutlnReg` параметра. `rgOutlnReg` Параметр <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> структуры. Этот процесс позволяет задавать различные характеристики скрытые области, например развернут или свернут определенного региона.  
  
> [!NOTE]
>  Следует с осторожностью скрытие символы новой строки. Скрытый текст должен расширять от начала первой строки до последнего символа в последней строке раздела, оставляя видимыми последним символом новой строки.  
  
## <a name="see-also"></a>См. также  
 [Как: обеспечивают поддержку скрытый текст в языковую службу прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)