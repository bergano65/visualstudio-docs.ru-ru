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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651cecb20604069c6e8ccc5a5c7b983ab43d7384
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190061"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в языковой службе прежних версий
При автоматическом форматировании языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить известную конструкцию кода.

## <a name="automatic-formatting-behavior"></a>Поведение автоматического форматирования
 Например, при вводе значения, *Если* языковая служба автоматически вставляет парные скобки или нажата клавиша ВВОД, языковая служба принудительно устанавливает точку вставки на новой строке на соответствующий уровень отступа в зависимости от того, открывается ли Предыдущая строка в новой области.

 Фильтр команд, используемый для оставшейся версии языковой службы, также можно использовать для автоматического форматирования. Можно также выделить Парные фигурные скобки, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>См. также раздел
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
