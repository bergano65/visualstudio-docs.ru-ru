---
title: Автоматическое форматирование в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74e92cac718c24245988f0e5bdbcbc05e2aee43d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002565"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службы прежних версий
Автоматическое форматирование, языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить конструкцию известных кода.  
  
## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования  
 Например, при вводе *Если*языковая служба автоматически вставляет парные фигурные скобки или при нажатии клавиши ВВОД, языковая служба заставляет курсор на новой строке на уровень отступов, в зависимости от ли предыдущая строка открывает новую область.  
  
 Команда фильтр, используемый для остальной части языковой службы можно использовать также для автоматического форматирования. Можно также выделить парные фигурные скобки, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)