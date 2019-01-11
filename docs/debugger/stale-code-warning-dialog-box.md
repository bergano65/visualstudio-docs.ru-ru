---
title: Устаревший код сообщения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82731ba2c22c18b880e8a035712280eb5e5afe68
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877462"
---
# <a name="stale-code-warning-dialog-box"></a>Предупреждение о необходимости обновления кода - диалоговое окно

Это диалоговое окно появляется, если в машинный код были внесены изменения, которые не удалось немедленно применить с использованием операции **Изменить и продолжить**. В результате часть машинного кода в текущем кадре стека является устаревшей. Дополнительные сведения см. в статье [Edit and Continue (Visual C++)](edit-and-continue-visual-cpp.md) (Изменить и продолжить (Visual C++)).

**Больше не показывать это окно**

Если установить этот флажок, операция "Изменить и продолжить" будет в дальнейшем применять изменения кода без запроса разрешения. Это предупреждение можно включить снова, если зайти в диалоговое окно **Параметры**, открыть папку **Отладка**, выбрать страницу **Изменить и продолжить** и выбрать **Предупреждение о необходимости обновления кода**.

## <a name="see-also"></a>См. также раздел

- [Поддерживаемые изменения кода (C++)](supported-code-changes-cpp.md)
- [Страница "Изменить и продолжить", папка "Отладка", диалоговое окно "Параметры"](edit-and-continue.md)