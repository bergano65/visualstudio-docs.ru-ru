---
title: Диалоговое окно предупреждения о необходимости обновления кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a89738446bf8c08680835ddccb7efa30c2f740f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694700"
---
# <a name="stale-code-warning-dialog-box"></a>Предупреждение о необходимости обновления кода - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это диалоговое окно появляется, если в машинный код были внесены изменения, которые не удалось немедленно применить с использованием операции **Изменить и продолжить**. В результате часть машинного кода в текущем кадре стека является устаревшей. Дополнительные сведения см. [в разделе руководство. Работа с устаревшим кодом](https://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Больше не показывать это окно**  
 Если установить этот флажок, операция "Изменить и продолжить" будет в дальнейшем применять изменения кода без запроса разрешения. Это предупреждение можно включить снова, если зайти в диалоговое окно **Параметры**, открыть папку **Отладка**, выбрать страницу **Изменить и продолжить** и выбрать **Предупреждение о необходимости обновления кода**.  
  
## <a name="see-also"></a>См. также:  
 [Поддерживаемые изменения кода (C++)](../debugger/supported-code-changes-cpp.md)   
 [Страница "Изменить и продолжить", папка "Отладка", диалоговое окно "Параметры"](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)
