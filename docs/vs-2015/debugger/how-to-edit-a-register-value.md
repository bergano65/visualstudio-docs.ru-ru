---
title: Практическое руководство. Изменение значения регистра | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ea1e932f7651439dcb9a1ff85094bd30e5239bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116170"
---
# <a name="how-to-edit-a-register-value"></a>Практическое руководство. Изменение значения регистра
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно "Регистры" доступно, только если включена отладка на уровне адреса в диалоговом окне **Параметры** в разделе **Отладка**.  
  
### <a name="to-change-the-value-of-a-register"></a>Чтобы изменить значение регистра  
  
1. В окне **Регистры** при помощи клавиши TAB или мыши переместите курсор на то значение, которое нужно изменить. Перед началом ввода курсор должен находиться впереди значения, которое требуется переписать.  
  
2. Введите новое значение.  
  
    > [!CAUTION]
    >  Изменение значений регистров (в особенности регистров EIP и EBP) может повлиять на выполнение.  
  
    > [!CAUTION]
    >  Изменение значений с плавающей запятой может привести к незначительной погрешности, связанной с преобразованием дробных компонентов из десятичной формы в двоичную. Даже кажущееся внешне безвредным редактирование может привести к изменениям некоторых младших бит в регистре с плавающей запятой.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)
