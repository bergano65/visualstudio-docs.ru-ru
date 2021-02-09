---
title: Автоматическое форматирование в языковой службе прежних версий | Документация Майкрософт
description: Сведения об автоматическом форматировании в языковой службе прежних версий, которая автоматически вставляет фрагмент кода при начале ввода известной конструкции кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de54f43ca8abc7547609882647e014cb3695da33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906060"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службе прежних версий
При автоматическом форматировании языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить известную конструкцию кода.

## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования
 Например, при вводе значения, *Если* языковая служба автоматически вставляет парные скобки или нажата клавиша ВВОД, языковая служба принудительно устанавливает точку вставки на новой строке на соответствующий уровень отступа в зависимости от того, открывается ли Предыдущая строка в новой области.

 Фильтр команд, используемый для оставшейся версии языковой службы, также можно использовать для автоматического форматирования. Можно также выделить Парные фигурные скобки, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>См. также раздел
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
