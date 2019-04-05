---
title: Устаревший код сообщения | Документация Майкрософт
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
ms.openlocfilehash: adb8bfdf5edb4f6aa04a53f051fafa9ef3793e10
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994245"
---
# <a name="stale-code-warning-dialog-box"></a>Предупреждение о необходимости обновления кода - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это диалоговое окно появляется, если в машинный код были внесены изменения, которые не удалось немедленно применить с использованием операции **Изменить и продолжить**. В результате часть машинного кода в текущем кадре стека является устаревшей. Дополнительные сведения см. в разделе [Как Работа с устаревшим кодом](http://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Больше не показывать это окно**  
 Если установить этот флажок, операция "Изменить и продолжить" будет в дальнейшем применять изменения кода без запроса разрешения. Это предупреждение можно включить снова, если зайти в диалоговое окно **Параметры**, открыть папку **Отладка**, выбрать страницу **Изменить и продолжить** и выбрать **Предупреждение о необходимости обновления кода**.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые изменения кода (C++)](../debugger/supported-code-changes-cpp.md)   
 [Страница "Изменить и продолжить", папка "Отладка", диалоговое окно "Параметры"](http://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)
