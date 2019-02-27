---
title: 'Практическое: изменение значения регистра | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ee5d0b36196c85d7c81b63503bfcc471d7664
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717122"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Практическое: изменение значения регистра (C#, C++, Visual Basic, F#)

Окно "Регистры" доступно, только если включена отладка на уровне адреса в диалоговом окне **Параметры** в разделе **Отладка**.

### <a name="to-change-the-value-of-a-register"></a>Чтобы изменить значение регистра

1.  В окне **Регистры** при помощи клавиши TAB или мыши переместите курсор на то значение, которое нужно изменить. Перед началом ввода курсор должен находиться впереди значения, которое требуется переписать.

2.  Введите новое значение.

    > [!CAUTION]
    >  Изменение значений регистров (в особенности регистров EIP и EBP) может повлиять на выполнение.

    > [!CAUTION]
    >  Изменение значений с плавающей запятой может привести к незначительной погрешности, связанной с преобразованием дробных компонентов из десятичной формы в двоичную. Даже кажущееся внешне безвредным редактирование может привести к изменениям некоторых младших бит в регистре с плавающей запятой.

## <a name="see-also"></a>См. также раздел
- [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)