---
title: "Автоматическое форматирование в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09ab8a948011cdc53516ec21f0d213852166956
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковую службу прежних версий
Автоматическое форматирование языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить конструкцию кода известных.  
  
## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования  
 Например, при вводе `if`языковой службы автоматически вставляет парные фигурные скобки или при нажатии клавиши ВВОД, языковой службы приводит к смещению курсор в новой строке уровень отступов в зависимости от того, следует ли приведенный выше строки открывает новую область.  
  
 Команда фильтр, используемый для остальной части языковой службы также может использоваться для автоматического форматирования. Можно также выделить парные фигурные скобки, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)