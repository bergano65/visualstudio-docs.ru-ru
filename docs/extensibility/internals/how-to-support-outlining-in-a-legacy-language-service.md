---
title: 'Как: поддерживает структуризация в языковую службу прежних версий | Документы Microsoft'
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
ms.openlocfilehash: f9880c5c255118478d15f34f9a9245a1c25d97fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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