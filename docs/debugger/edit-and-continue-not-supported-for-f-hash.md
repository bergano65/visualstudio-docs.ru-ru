---
title: Изменить и продолжить, не поддерживается для F# | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 856940231e65932b208c83bf4ff1231395b04382
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838077"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Функция "Изменить и продолжить" не поддерживается для языка F# #
Операция "Изменить и продолжить" не поддерживается при отладке кода F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Во время сеанса отладки изменения кода не применяются. Поэтому любое изменение кода F# во время отладки может привести к несоответствию исходного и отлаживаемого кода.
