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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a686cf91a515d2b7b59d87d7b3ca8e92d4e54c59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871992"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Функция "Изменить и продолжить" не поддерживается для языка F# #
Операция "Изменить и продолжить" не поддерживается при отладке кода F#. Редактирование кода на языке F# во время сеанса отладки возможно, но его следует избегать. Во время сеанса отладки изменения кода не применяются. Поэтому любое изменение кода F# во время отладки может привести к несоответствию исходного и отлаживаемого кода.
