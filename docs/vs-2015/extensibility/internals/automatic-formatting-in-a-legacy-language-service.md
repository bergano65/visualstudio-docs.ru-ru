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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157271"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При автоматическом форматировании языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить известную конструкцию кода.  
  
## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования  
 Например, при вводе `if` языковая служба автоматически вставляет парные скобки или, если нажата клавиша ВВОД, языковая служба принудительно устанавливает для точки вставки на новой строке соответствующий уровень отступа, в зависимости от того, открывается ли Предыдущая строка в новой области.  
  
 Фильтр команд, используемый для оставшейся версии языковой службы, также можно использовать для автоматического форматирования. Можно также выделить Парные фигурные скобки, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>См. также:  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
