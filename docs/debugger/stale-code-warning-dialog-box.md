---
title: Устаревший код сообщения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: f1e212602b317127cfd14adcd246a23cdd92ed86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281797"
---
# <a name="stale-code-warning-dialog-box"></a>Предупреждение о необходимости обновления кода - диалоговое окно
Это диалоговое окно отображается после внесения изменений в машинный код, который **изменить и продолжить** не удалось немедленно применить. В результате часть машинного кода в текущем кадре стека является устаревшей. Дополнительные сведения см. в разделе [как: работа с устаревшим кодом](/visualstudio/debugger/edit-and-continue-visual-cpp#bkmk_how_to_work_with_stale_code).  
  
 **Больше не показывать это диалоговое окно**  
 Если установить этот флажок, операция "Изменить и продолжить" будет в дальнейшем применять изменения кода без запроса разрешения. Можно включить это предупреждение снова, выбрав **параметры** диалоговом окне открытия **Отладка** папку, нажав кнопку **изменить и продолжить** страницы и выбрав **Предупреждать об устаревшем коде**.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые изменения кода (C++)](../debugger/supported-code-changes-cpp.md)   
 [Страница "Изменить и продолжить", папка "Отладка", диалоговое окно "Параметры"](/visualstudio/debugger/edit-and-continue)