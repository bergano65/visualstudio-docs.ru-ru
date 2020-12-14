---
title: Функция "Изменить и продолжить" не поддерживается для языка F# | Документация Майкрософт
description: Функция "Изменить и продолжить" не поддерживается при отладке для языка F#. Изменения, внесенные в код в процессе отладки, не применяются к исходному коду, в результате чего код, для которого выполняется отладка, не соответствует исходному.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863092"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Функция "Изменить и продолжить" не поддерживается для языка F# #
Операция "Изменить и продолжить" не поддерживается при отладке кода F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Во время сеанса отладки изменения кода не применяются. Поэтому любое изменение кода F# во время отладки может привести к несоответствию исходного и отлаживаемого кода.
