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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851159"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Функция "Изменить и продолжить" не поддерживается для языка F# #
Операция "Изменить и продолжить" не поддерживается при отладке кода F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Во время сеанса отладки изменения кода не применяются. Поэтому любое изменение кода F# во время отладки может привести к несоответствию исходного и отлаживаемого кода.
