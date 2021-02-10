---
title: Изменение значения регистра | Документация Майкрософт
description: Сведения об изменении содержимого регистра, изменив его значение в окне "Регистры" (доступно, только если включена отладка на уровне адреса).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4187be3bd4d5d2099374acea58d86bd093538ef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917381"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Практическое руководство. Изменение значения регистра (C#, C++, Visual Basic, F#)

Окно "Регистры" доступно, только если включена отладка на уровне адреса в диалоговом окне **Параметры** в разделе **Отладка**.

### <a name="to-change-the-value-of-a-register"></a>Чтобы изменить значение регистра

1. В окне **Регистры** при помощи клавиши TAB или мыши переместите курсор на то значение, которое нужно изменить. Перед началом ввода курсор должен находиться впереди значения, которое требуется переписать.

2. Введите новое значение.

    > [!CAUTION]
    > Изменение значений регистров (в особенности регистров EIP и EBP) может повлиять на выполнение.

    > [!CAUTION]
    > Изменение значений с плавающей запятой может привести к незначительной погрешности, связанной с преобразованием дробных компонентов из десятичной формы в двоичную. Даже кажущееся внешне безвредным редактирование может привести к изменениям некоторых младших бит в регистре с плавающей запятой.

## <a name="see-also"></a>См. также
- [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)