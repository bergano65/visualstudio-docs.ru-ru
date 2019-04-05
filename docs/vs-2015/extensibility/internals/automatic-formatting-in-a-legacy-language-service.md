---
title: Автоматическое форматирование в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994294"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Автоматическое форматирование, языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить конструкцию известных кода.  
  
## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования  
 Например, при вводе `if`языковая служба автоматически вставляет парные фигурные скобки или при нажатии клавиши ВВОД, языковая служба заставляет курсор на новой строке на уровень отступов в зависимости от того, следует ли выше строки открывает новую область.  
  
 Команда фильтр, используемый для остальной части языковой службы можно использовать также для автоматического форматирования. Можно также выделить парные фигурные скобки, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
