---
title: 'Практическое: изменение значения регистра | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 465ecd4e8003b82a0a7dfbab33004ef2b80d7f32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568182"
---
# <a name="how-to-edit-a-register-value"></a>Практическое руководство. Изменение значения регистра
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: изменение значения зарегистрировать](https://docs.microsoft.com/visualstudio/debugger/how-to-edit-a-register-value).  
  
Окно "Регистры" доступно только в том случае, если включена отладка на уровне адреса в **параметры** диалоговом окне **Отладка** узла.  
  
### <a name="to-change-the-value-of-a-register"></a>Чтобы изменить значение регистра  
  
1.  В **регистрирует** окно, можно использовать клавишу TAB или мыши переместите курсор на значение, вы хотите изменить. Перед началом ввода курсор должен находиться впереди значения, которое требуется переписать.  
  
2.  Введите новое значение.  
  
    > [!CAUTION]
    >  Изменение значений регистров (в особенности регистров EIP и EBP) может повлиять на выполнение.  
  
    > [!CAUTION]
    >  Изменение значений с плавающей запятой может привести к незначительной погрешности, связанной с преобразованием дробных компонентов из десятичной формы в двоичную. Даже кажущееся внешне безвредным редактирование может привести к изменениям некоторых младших бит в регистре с плавающей запятой.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)





