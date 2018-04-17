---
title: Автоматическое форматирование в языковую службу прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e052c62afcf9551cc54373da15071fb3903fe950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковую службу прежних версий
Автоматическое форматирование языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить конструкцию кода известных.  
  
## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования  
 Например, при вводе `if`языковой службы автоматически вставляет парные фигурные скобки или при нажатии клавиши ВВОД, языковой службы приводит к смещению курсор в новой строке уровень отступов в зависимости от того, следует ли приведенный выше строки открывает новую область.  
  
 Команда фильтр, используемый для остальной части языковой службы также может использоваться для автоматического форматирования. Можно также выделить парные фигурные скобки, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)