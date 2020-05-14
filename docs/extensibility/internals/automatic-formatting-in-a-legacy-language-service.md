---
title: Автоматическое форматирование в услуге Legacy Language Service (ru) Документы Майкрософт
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
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709982"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Автоматическое форматирование в устаревшей языковой службе
При автоматическом форматировании языковая служба автоматически вставляет фрагмент кода, когда пользователь начинает вводить известную конструкцию кода.

## <a name="automatic-formatting-behavior"></a>Автоматическое поведение форматирования
 Например, при вводе, *если,* языковая служба автоматически вставляет соответствующие скобки, или если вы нажимаете клавишу ENTER, языковая служба заставляет точку вставки на новой строке к соответствующему уровню отступа, в зависимости от того, открывает ли предыдущая строка новую область.

 Командный фильтр, используемый для остальной части языковой службы, также может быть использован для автоматического форматирования. Вы также можете выделить соответствующие скобки, позвонив. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>

## <a name="see-also"></a>См. также
- [Разработка устаревшего языкового сервиса](../../extensibility/internals/developing-a-legacy-language-service.md)
